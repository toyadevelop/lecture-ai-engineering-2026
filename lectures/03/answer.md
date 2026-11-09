# 第3回 解答

## 演習

- 第1回（素のLLM）とエージェントの回答の違い：単に予測して文章を生成するだけでなく検索を挟んで返答を返す。
- `--trace` で見えたツール呼び出し（ツール名と引数）：get_lecture_summary({'lecture': 0})
- 1つの質問での LLM 呼び出し回数（`requests`）：2
- 追加したツールと、docstring に書いた説明：def make_quiz(lecture: int) -> str:
    """指定した回の用語から1つ選び、確認問題と答えを返す。

    「第２回の確認問題を出して」のように、復習用の問題を求められたときに使う
    """
    terms = [term for term in load_glossary() if term["lecture"] == lecture]
    if not terms:
        return f"第{lecture}回の用語が用語集にありません。"

    term = random.choice(terms)
    return json.dumps(
        {
            "question": f"「{term['term']}」の意味は？",
            "answer": term["definition"],
        },
        ensure_ascii=False,
    )


## 宿題

- 取り組んだレベル：基礎 
- やったこと：
- 結果：
- 気づき・疑問：
