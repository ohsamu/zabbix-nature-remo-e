# zabbix-nature-remo-e

* ZabbixのNature Remo E lite用テンプレート
* 1分間隔の瞬時電力計測値グラフ
  - 2kW超えトリガー
* 30分間隔の積算電力量計測値(正方向)差分グラフ


## 使い方
* テンプレートをインポートする
* 適当なホストを作成する
* MACROで ```{$API_KEY}``` を設定する


## discovery動作
* discoveryで https://api.nature.global/1/appliances を取得
* ```"type": "EL_SMART_METER"``` な appliance を見つけて ```id``` と ```name``` を取得


## アイテム・グラフ
* 1分ごとにJSONデータを取得
  - そのJSONから ```measured_instantaneous``` をグラフ化
* 30分ごとにJSONデータを取得， ```normal_direction_cumulative_electric_energy``` の前回との差分をグラフ化


## 考慮していないこと
* ```coefficient``` は1固定
* ```cumulative_electric_energy_unit``` は1(0.1kWh)固定
  - https://developer.nature.global/jp/how-to-calculate-energy-data-from-smart-meter-values

