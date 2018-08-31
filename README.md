# Kylin_Bancor_Points Test Guide

## Inspiration

EOS Ram System

大家好，我们编写了一个基于Bancor兑换模式的Kylinspoints，目前部署在`kylinspoints` 这个account上，下面是测试的指南，可以用我们在麒麟网上的EOS币兑换KLP，可反向兑换 (在Connector里面含有EOS的前提下)。

我们计划给麒麟币的兑换配上UI，希望大家有兴趣的话，去测试下，并提出宝贵的意见

>  这项目目前是alpha版，可能还有很多问题

# Manual Test Guide



## KLP Bancor Token 简介：

账户**kypsmintager**：用于铸币，部署klp.token 智能合约

账户**kylinspoints: ** 用于转账，部署klp.connector 智能合约

- 测试账户向`kylinspoints`转 EOS，会返回KLP token
- 测试账户向`kylinspoints`转 KLP，会返回EOS token

```
cleos -u http://api-kylin.eoshenzhen.io:8890 kylinspoints klp.contracts/build/klp.token
```

# 1.1. Preparation

   <http://faucet.cryptokylin.io/create_account?XXXX>

   <http://faucet.cryptokylin.io/get_token?XXXX>

## 2. Transfer EOS to kylinspoints account

```
cleos -u http://api-kylin.eoshenzhen.io:8890 push action kylinspoints transfer '["kylinspoints", "testsaccount", "1.234 EOS", "convert KLP"]' -p kylinspoints
```

## 3. Transfer KLP to kylinspoints account

```
cleos -u http://api-kylin.eoshenzhen.io:8890 push action kylinspoints transfer '["testsaccount", "kylinspoints", "1000 KLP", "transfer KLP"]' -p testsaccount
```



## 可视化操作

```
curl --request POST \
  --url http://api-kylin.eoshenzhen.io:8890/v1/chain/get_table_rows \
  --data '{"code":"kylinspoints","scope":"kylinspoints","table":"klpmarket", "json":"true"}'
```

## UI 

