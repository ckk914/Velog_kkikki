<p>공부하기 좋게
메모할 수 있도록 직접 구현한 프로젝트 파해치며 정리</p>
<p>[수정부분으로 정리]</p>
<blockquote>
<p>DB</p>
</blockquote>
<pre><code class="language-java">Table: tbl_memo

Columns:
memonum int(8) AI PK
memoText varchar(150)
reg_date datetime
</code></pre>
<blockquote>
<p>메모 엔터티</p>
</blockquote>
<pre><code class="language-java">package com.test.mvc.entity;

import lombok.*;
import org.checkerframework.checker.units.qual.N;

import java.time.LocalDateTime;

@Getter@ToString
@EqualsAndHashCode
@NoArgsConstructor
@AllArgsConstructor
@Builder
public class Memo {
    private String memoNum;                 //index
    private String memoText;                // memo content
    private LocalDateTime regDate;      //register Date

}
</code></pre>
<blockquote>
<p>컨트롤러 </p>
</blockquote>
<pre><code class="language-java">package com.test.mvc.controller;

import com.test.mvc.dto.MemoModifyDto;
import com.test.mvc.dto.MemoPostDto;
import com.test.mvc.entity.Memo;
import com.test.mvc.service.MemoService;
import lombok.RequiredArgsConstructor;
import lombok.extern.slf4j.Slf4j;
import org.springframework.http.ResponseEntity;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.validation.BindingResult;
import org.springframework.validation.FieldError;
import org.springframework.validation.annotation.Validated;
import org.springframework.web.bind.annotation.*;

import java.util.HashMap;
import java.util.List;
import java.util.Map;


@Controller
@RequestMapping("/")
@RequiredArgsConstructor
@Slf4j
public class MemoController {
    //서비스 통해 위임하여 조회나 기타등등
    private final MemoService memoService;</code></pre>
<p>...</p>
<blockquote>
<p>컨트롤러 수정 부분</p>
</blockquote>
<pre><code class="language-java"> // ▽ put patch 동시 사용 방법.~!⭐️
    @RequestMapping(method = {RequestMethod.PUT, RequestMethod.PATCH})
    public ResponseEntity&lt;?&gt; modify(
           @Validated @RequestBody MemoModifyDto dto
            , BindingResult result      //검증 객체
    ) {

        log.info("/api/v1/replies : PUT, PATCH");       //PUT 타입으로 넘겨주면 받는다~!
        log.debug("parameter: {}", dto);

        //@Validated 건 곳에서 dto 들어가면   @NotNull @NotBlink 인지 검사
        if (result.hasErrors()) {
            Map&lt;String, String&gt; errors = makeValidationMessageMap(result);

            return ResponseEntity
                    .badRequest()
                    .body(errors);
        }



        List&lt;Memo&gt; mList = memoService.modify(dto);
        return ResponseEntity.ok().body(mList);
    }</code></pre>
<blockquote>
<p>MemoModifyDto</p>
</blockquote>
<pre><code class="language-java">package com.test.mvc.dto;


import lombok.*;

import javax.validation.constraints.NotBlank;
import javax.validation.constraints.NotNull;

@Getter
@ToString
@NoArgsConstructor
@AllArgsConstructor
@EqualsAndHashCode
@Builder
public class MemoModifyDto {
    @NotNull
    private long mno;
    @NotNull
    private String newText;
}
</code></pre>
<p>프론트 부분 Jsp/ <code>&lt;script&gt;</code> 부분 </p>
<pre><code class="language-java">else if (
              e.target.classList.contains(`edit-btn`) ||
              e.target.classList.contains(`fa-pencil-alt`) ||
              e.target.classList.contains(`fa-check`)
            ) {
              //# 수정
              // console.log("수정 클릭!!");

              if (
                e.target.classList.contains(`edit-btn`) ||
                e.target.classList.contains(`fas`)
              ) {
                const $card = e.target.closest(`.card`);

                const $cardFirstChild = $card.firstElementChild;
                console.log("card=&gt;", $card);
                const $cardButtons = $card.children[2];
                console.log("cb=&gt;", $cardButtons);
                const $editButton = $cardButtons.children[0];
                console.log($editButton);

                const $icon = $editButton.children[0];

                if ($icon.classList.contains("fa-pencil-alt")) {
                  //아이콘 변경
                  $icon.classList.remove("fa-pencil-alt");
                  $icon.classList.add("fa-check");
                  // 태그 변경
                  console.log($cardFirstChild);
                  var newSpan = document.createElement("textarea");
                  newSpan.classList.add("card-content");
                  newSpan.textContent = $cardFirstChild.textContent;
                  $cardFirstChild.parentNode.replaceChild(
                    newSpan,
                    $cardFirstChild
                  );
                } else if ($icon.classList.contains("fa-check")) {
                  console.log("저장 ㄱ");
                  $icon.classList.remove("fa-check");
                  $icon.classList.add("fa-pencil-alt");

                  //UI 업데이트
                  const $cardFirstChild2 = $card.firstElementChild;
                  var newSpan = document.createElement("div");
                  newSpan.classList.add("card-content");
                  newSpan.textContent = $cardFirstChild2.value;
                  console.log("바꿀내용:", $cardFirstChild2.value);
                  $cardFirstChild2.parentNode.replaceChild(
                    newSpan,
                    $cardFirstChild2
                  );

                  //db 처리를 위한 넘버 소환!
                  const mno = $card.dataset.mno;
                  console.log(mno);
                  const newText = $cardFirstChild2.value;
                  fetchModifyMemo(mno, newText);
                }

                // console.log('editList=&gt;', $icon.classList);
                // const $editBtn = $cardButtons.closest(`.edit-btn`);
                // console.log('sss=&gt;', $editBtn);
                // const content = $mno.firstElementChild.content;
                // console.log(e.target.classList);
                // console.log($card);
              }
            }
          });
        // });</code></pre>
<p>frontEnd 부분 렌더링 부분 발췌 <code>&lt;body&gt;</code> 내용</p>
<pre><code class="language-java">&lt;/div&gt;
      &lt;div class="memo-total-List"&gt;
        &lt;c:if test="${mList.size() &gt; 0}"&gt;
          &lt;c:forEach var="memo" items="${mList}"&gt;
            &lt;div class="memo-wrapper"&gt;
              &lt;section class="card" data-mno="${memo.memoNum}"&gt;
                &lt;div class="card-content"&gt;${memo.memoText}&lt;/div&gt;
                &lt;div class="card-time"&gt;등록시간: ${memo.regDate}&lt;/div&gt;

                &lt;div class="card-buttons"&gt;
                  &lt;button class="edit-btn"&gt;
                    &lt;i class="fas fa-pencil-alt"&gt;&lt;/i&gt;
                  &lt;/button&gt;
                  &lt;button class="delete-btn"&gt;
                    &lt;i class="fas fa-trash-alt"&gt;&lt;/i&gt;
                  &lt;/button&gt;
                &lt;/div&gt;
              &lt;/section&gt;
            &lt;/div&gt;
          &lt;/c:forEach&gt;
        &lt;/c:if&gt;
      &lt;/div&gt;

```java

 //db 처리를 위한 넘버 소환!
                  const mno = $card.dataset.mno;
                  console.log(mno);
                  const newText = $cardFirstChild2.value;
                  fetchModifyMemo(mno, newText);
</code></pre>
<pre><code class="language-java">// # 수정
        const fetchModifyMemo = async (mno, newText) =&gt; {
          const payload = {
            mno: mno,
            newText: newText,
          };
          console.log("payload", payload);
          console.log("url", url);
          const res = await fetch(url, {
            method: "PUT",
            headers: {
              "content-type": "application/json",
            },
            body: JSON.stringify(payload),
          });

          if (res.status === 403) {
            alert("로그인이 필요한 서비스입니다.");
            // window.location.href = '/members/sign-in';
            return;
          }
        };
</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/0e3898ce-9773-43b9-b00d-4153eaef56e4/image.png" /></p>
<p>찍힌 로그</p>
<pre><code>저장 ㄱ
바꿀내용: 111222
82
payload {mno: '82', newText: '111222'}</code></pre><p>MemoMapper.xml</p>
<pre><code class="language-java">&lt;update id="modify"&gt;
        UPDATE tbl_memo
        SET memoText = #{newText}
        WHERE memonum = #{mno}
    &lt;/update&gt;</code></pre>
<p>실제 컬럼은 memoText 이기 때문에 
<code>#{}</code>을 사용해서 값을 컬럼에 맞게 넣어줌</p>
<p>Columns:
memonum int(8) AI PK
memoText varchar(150)
reg_date datetime</p>
<hr />