# Databricksの使い方
 - Azure portal からワークスペース／リソースグループ／リージョン／サブスクリプションを選ぶ
 - リソースが作ら荒れたあとに、"Launch Workspace"で開発ワークスペースｗ呼び出せる。
 - AzureBLOB Storage と接続  
 以下のコマンドを使う。マウントしたディレクトリを使うときは、dbfs:/mnt/<ディレクトリ名>

  ```
  dbutils.fs.mount(
  source = "wasbs://<コンテナー名>@<ストレージ名>.blob.core.windows.net",
  mount_point = "/mnt/<任意のディレクトリ名>",　##マウントするDBFSのパス、使うときはdbfs:/mnt/<ディレクトリ名>
  extra_configs = {"fs.azure.account.key.<ストレージ名>.blob.core.windows.net":"<アクセスキー>"})
  ```
  
  sparkのデータフレーム型にデータを入れる場合は、`spark.read`クラスの関数を使うと良い
  
  csvなら`spark.read.csv(<data_path>)`  
  jasonなら`spark.read.json(<data_path>)`  
  などなど。。。
  
PythonやScalaのNotebookから、`%sh`ステートメントでシェルを呼び出すこともできる。
例えばGithubのAPIを呼び出すなら、以下のように書く
```
%sh %sh curl "https://api.github.com/events " -o response -#
```

##補記
databricksでJavaサポートといいつつJAR読めるだけじゃん。
https://forums.databricks.com/questions/1564/can-i-run-java-in-a-scala-notebook.html


---  
参考  
 BLOBのマウント
  https://qiita.com/sae_py_/items/f1d40cc10fd67fd07a94
 Dataframeの作成
  https://ohke.hateblo.jp/entry/2018/09/01/234500