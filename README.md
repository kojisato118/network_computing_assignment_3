# network_computing_assignment_3

## 確認手順
### ViertualBoxにいれる
[ovaファイルをDL](https://drive.google.com/open?id=0B3wluWBRnMf5aXB4RXUtMWE4Wms)

http://qiita.com/kojisato118/items/ad8667266c846eb5e642    
この辺参考にしてください

### 解析サーバー起動
- ```$ ssh ryu@192.168.56.101```
- ```$ cd server/file-analizer```
- ```$ bundle exec rails s -b 10.0.2.15```

### mininet起動
- ```$ sudo mn --topo single,1 --mac --switch ovsk --controller remote -x --nat```

### s1の設定
- ```$ ovs-vsctl set Bridge s1 protocols=OpenFlow13 (起動したswitch:s1と書かれたxterm)```

### c0の設定
- ```$ ryu-manager --verbose ryu/ryu/app/network_computing.py```

### h1の設定
- ```$ cd network_computing```
- ```$ curl -X POST -F file=@test.csv http://10.0.2.15:3000/api/v1/dummy```

### その他
- ```$ curl -X POST -d file_name=test.csv http://10.0.2.15:3000/api/v1/files```
- ```$ curl -X DELETE -d file_name=test.csv http://10.0.2.15:3000/api/v1/files```


