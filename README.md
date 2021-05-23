### スモールスケールでの自動運転
![image](https://user-images.githubusercontent.com/44959708/71329934-435c3200-256d-11ea-9cf0-b2c2dff08840.png)

上記の車に道路や標識を認識させ、そして自動で速度や方向を変化させることを目標としたプロジェクト。
私はこのプロジェクトで標識認識の部分を担当した。

今回、認識する標識はこの三つに設定した。左から、速度変更、走行開始、走行停止である。
![image](https://user-images.githubusercontent.com/44959708/71330686-b1a2f380-2571-11ea-8454-5f6d7b5ae19a.png)

標識認識の流れを説明する。
![image](https://user-images.githubusercontent.com/44959708/71330447-7a801280-2570-11ea-8575-634d53ff0622.png)
![image](https://user-images.githubusercontent.com/44959708/71330757-0a728c00-2572-11ea-84ee-9eb76355ffd4.png)

実際の道路でも標識は進行方向に対して左側に設置されるため、元画像から左上を切り出す。

次に、SelectiveSearch※を使用して標識が存在すると思わしき候補領域を抜き出す。

最後に、事前にGTRSBのデータセットで学習させたVGG19のモデルを抜き出した領域に適応する。設定した閾値を超えなかった場合は標識は存在しないと判定する。

他の物体検出(YOLO,SSD)と比較して精度は低いもの※2となったが、画像をアノテーションした学習データを用意する必要が無いので、手軽さで言えばこのシステムに利点があると思われる。

<br><br>
※1今回SelectiveSearchを行うにあたって、下記のライブラリを使用した。<br>
https://github.com/AlpacaDB/selectivesearch <br>
LICENSE:
Copyright (c) 2015-2016 AlpacaDB
Copyright (c) 2016 Oussama ENNAFII

https://opensource.org/licenses/mit-license.php

※2レポート参照
