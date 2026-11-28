# 第6回 解答

## 演習

<!-- [tool call] の行は、表示された行をそのまま貼り付けてください。終わらなかった STEP は、空欄のままでかまいません。 -->

- STEP 1 のツールの名前：search_materials、glossary_search_glossary
- STEP 2 の [tool call]： [tool call] glossary_search_glossary({'query': '3レベル'})
- STEP 3 の [tool call]：[tool call] fetch_fetch({'url': 'https://modelcontextprotocol.io/'}) [tool call] glossary_search_glossary({'query': 'MCP'})
- STEP 4 の [tool call]： [tool call] aws_aws___search_documentation({'search_phrase': 'Amazon S3 Versioning overview', 'topics': ['general']})
- 気づき・疑問：MCPを利用すると、AIエージェントから外部のツールを 呼び出せることが分かった。 用語集検索、Webページ取得、AWSドキュメント検索など、 異なるMCPサーバーのツールを利用できた。 また、質問内容に応じてAIが適切なツールを選択することを確認した。

## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->

- 取り組んだレベル：基礎 
- やったこと：app/mcp_server.pyを編集し、 get_lecture_summaryをMCPツールとして追加した。 server.tool()(tools.get_lecture_summary)を登録した。
- 結果：glossary_get_lecture_summaryがツール一覧に表示された。 第2回の講義内容を質問したところ、 glossary_get_lecture_summaryが呼び出され、 ファインチューニングとLoRAについて回答が得られた。 自動テストも実行し、24 passedとなった。
- 気づき・疑問：Pythonの関数をMCPツールとして登録することで、 AIエージェントから利用できるようになることを学んだ。 また、--traceを使うと、実際にどのツールが 呼び出されたか確認できることが分かった。