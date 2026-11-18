# 商品管理

架空の店舗の商品をJSONから読み込み、コンソールに表示するPythonプログラムです。商品10件の一覧、在庫が3未満の商品一覧、終了操作ができます。

自主課題の条件は[ TASK.md ](TASK.md)にあります。新しい機能を完成させたら、このREADMEの機能と操作方法も更新してください。

## 取得

履歴とブランチを使うため、Gitでクローンします。ZIPのダウンロードでは、この演習に必要な履歴を取得できません。

```bash
git clone https://github.com/shigorefu-hirocom/1-python-copilot-branch-practice.git
cd 1-python-copilot-branch-practice
```

このフォルダーをVS Codeで開きます。以後のコマンドは、main.pyがあるフォルダーで実行します。

## 準備と起動

Python 3.10以上とGitを使います。プログラムは標準ライブラリだけで動きます。テストにはrequirements.txtのpytestを使います。

Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe main.py
.\.venv\Scripts\python.exe -m pytest -q
```

macOSのターミナル:

```bash
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python main.py
.venv/bin/python -m pytest -q
```

以後、pythonと短く書いたコマンドも、この仮想環境のPythonで実行します。VS Codeで.venvのPythonを選ぶか、上記の実行ファイルのパスを使ってください。

## メニュー

| 入力 | mainの動作 |
| --- | --- |
| 1 | 商品一覧を表示する |
| 2 | 在庫不足の商品を表示する |
| 0 | 終了する |

在庫不足の商品は、stockが3未満の商品です。在庫0、1、2の商品を対象とし、在庫3の商品は対象外です。表示は通常の商品一覧と同じ形式で、JSONの順番を保ちます。対象がない場合は、「該当する商品はありません。」と表示します。


## ファイルとクラス

| ファイル | 役割 |
| --- | --- |
| product.py | Product。id、name、category、price、stockを持ち、info()で表示用の文字列を返す |
| storage.py | load_products()がJSONを読み、Productのリストを返す |
| inventory.py | Inventoryが商品リストを保持し、get_all()で一覧のコピー、get_low_stock()で在庫不足の商品を返す |
| main.py | 商品の読み込み、メニュー、商品一覧と在庫不足商品の表示 |
| data/products.json | 架空の商品10件 |
| tests/test_base.py | 既存の動作を確認するテスト |
| requirements.txt | テスト用ライブラリ |
| AGENTS.md | エージェントに伝える作業ルール |

main.pyがload_products()の結果をInventoryへ渡し、取得したProductのinfo()を使って一覧を表示します。授業で扱ったクラス、関数、繰り返し、JSONを使った構成です。

## 詳しい資料

- [基本の操作](docs/usage.md)
- [データの意味と確認用の値](docs/data.md)
- [テストと手動確認](docs/testing.md)
- [作業記録](docs/work_log.md)
