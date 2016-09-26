# CFN-Your-VPC
提供幾種CloudFormation可用的基本VPC架構。
##比較
CloudFormation VS Wizzard, Step-by-step
    | 水果        | 价格    |  数量  |
    | --------   | -----:   | :----: |
    | 香蕉        | $1      |   5    |
    | 苹果        | $1      |   6    |
    | 草莓        | $1      |   7    |
##架構
###**三層式架構VPC**(包含DMZ、Application、Database三層)
1. 基本型的VPC架構: 建立VPC、Subnet、Route Table、基本的NACL、常用的Security Group。
2. 加入跳板機的VPC架構: 除了基本元件外，額外建立一台可以設定連線來源的跳板機(Bastion Server)，使維護者可以透過跳板機進入Application和Database層的主機或是DB。
3. 加入NAT Gateway的VPC架構: 除了基本元件外，額外建立"兩個"NAT Gateway，提供給Application層的主機可以透過NAT Gateway主動外連進行防毒、作業系統更新或是其他資料交換。(建立兩個NAT GW的原因是NAT GW不是跨可用區的服務，意味著必須要在各可用區中建立NAT GW才能保證單AZ毀損的狀況下維持服務的可用性。)
4. 加入S3 Endpoint的VPC架構: 除了基本元件外，額外建立S3 Endpoint，提供給Application層的主機連線至該Region的S3服務節點的能力。(不使用S3 Endpoint的情況下，必須要讓主機透過網際網路連線至S3。無法透過VPC內部連線至S3。)
5. 安全性較高的VPC架構: 建立VPC、Subnet、Route Table、進階的NACL、Security Group。(參照AWS NACL、Security Group的建議和筆者的經驗調整規則)In Process.........

###**兩層式架構VPC**(包含DMZ、Trust Zone兩層)
1. In Process.........

##使用
###AWS Web Console

###AWS CLI

##備註
CloudFormation在2016/09/16支援了YAML格式，後續也會陸續提供YAML格式的範本。(2016/09/26)
# CFN-Your-VPC
Provide several type AWS VPC architecture with cloudformation. Stop create VPC by using wizzard or step-by-step right now.
