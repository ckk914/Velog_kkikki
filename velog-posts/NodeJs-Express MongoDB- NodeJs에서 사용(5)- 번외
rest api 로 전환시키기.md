<pre><code class="language-java">import express from "express";
import nunjucks from "nunjucks";
import bodyParser from "body-parser";
import fs from "fs";
import path from "path"; // 추가된 부분
import { error, log } from "console";
import mongoose from "mongoose";
//resolve() : 현재 작업 디렉토리의 절대 경로를 반환
const __dirname = path.resolve();

const app = express();

//file path
// join을 통해서 경로들을 합쳐줌 __dirname :실행 경로 + /data/writing.json
const filePath = path.join(__dirname, "data", "writing.json");
console.log("경로는?" + filePath);

// body parser set
//서버에서 쉽게 접근하고 처리할 수 있도록 함
app.use(bodyParser.urlencoded({ extended: false })); // express 기본 모듈 사용
app.use(bodyParser.json());

// view engine set
app.set("view engine", "html"); // main.html -&gt; main(.html)

// nunjucks (템플릿 엔진을 설정) views 디렉토리
nunjucks.configure("views", {
  watch: true, // html 파일이 수정될 경우, 다시 반영 후 렌더링
  express: app,
});
//mongoose Connect (주소 작성)
mongoose
  .connect("mongodb://127.0.0.1:27017")
  .then(() =&gt; console.log("DB 연결 성공"))
  .catch((e) =&gt; console.error(e));

//mongoose set
//스키마 기능을 사용
const { Schema } = mongoose;

const WriteSchema = new Schema({
  title: String,
  contents: String,
  date: {
    type: Date,
    default: Date.now,
  },
});
// 모델은 Writing이라는 이름으로 WriteSchema를 갖게 된다.
const Writing = mongoose.model("Writing", WriteSchema);

//-------------------------------------
// GET
//-------------------------------------
// middleware
// main page GET
app.get("/", async (req, res) =&gt; {
  let writings = await Writing.find({});
  res.json(writings);
});

app.get("/write", (req, res) =&gt; {
  res.render("write");
});

//-------------------------------------
// write
//-------------------------------------
app.post("/write", async (req, res) =&gt; {
  const title = req.body.title;
  const contents = req.body.contents;

  const writing = new Writing({
    title: title,
    contents: contents,
  });

  try {
    await writing.save();
    console.log("Success");
    res.status(201).json(writing);
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: "Internal Server Error" });
  }
});

//-------------------------------------
// 상세 페이지
//-------------------------------------
//디비에서 데이터를 가져오기 위해 async 를 붙임
app.get("/detail/:id", async (req, res) =&gt; {
  const id = req.params.id;
  try {
    const detail = await Writing.findOne({ _id: id });
    res.json(detail);
  } catch (err) {
    console.log(err);
    res.status(500).json({ error: "Internal Server Error" });
  }
})

//-------------------------------------
// edit =&gt; get
//-------------------------------------
app.get("/edit/:id", async (req, res) =&gt; {
  const id = req.params.id;
  try {
    const edit = await Writing.findOne({ _id: id });
    res.json(edit);
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: "Internal Server Error" });
  }
});

//-------------------------------------
// edit =&gt; post
//-------------------------------------
app.put("/edit/:id", async (req, res) =&gt; {
  const id = req.params.id;
  const title = req.body.title;
  const contents = req.body.contents;

  try {
    const edit = await Writing.replaceOne(
      { _id: id },
      { title: title, contents: contents }
    );
    console.log("update success");
    res.json({ id: id, title: title, contents: contents });
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: "Internal Server Error" });
  }
});

//-------------------------------------
// delete =&gt; post
//-------------------------------------
app.delete('/delete/:id', async (req, res) =&gt; {
  const id = req.params.id;

  try {
    await Writing.deleteOne({ _id: id });
    console.log('delete success');
    res.status(204).send();
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: "Internal Server Error" });
  }
});

//-----------------------------------
app.listen(3000, () =&gt; {
  console.log("Server is running🐶");
});

</code></pre>
<p>기존에 res.render 하던건 화면을 직접 그려주는 것인데,</p>
<blockquote>
<p>res.json(writings);</p>
</blockquote>
<ul>
<li>json으로 response로 해주어, 다른 툴로 화면에 그릴 수 있게 할 수 있다.</li>
</ul>