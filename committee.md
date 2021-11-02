# Избираемый комитет и управление параметрами блокчейна

## Создание нового члена комитета
Основные параметры блокчейна, такие как комиссии за операции, зарплата витнесам и воркерам, время сборки блока, время обслуживания и так далее (подробнее с которыми можно ознакомиться в коде ядра) можно изменять без проведения хардфорка, с помощью такого избираемого органа как комитет. Комитет это избираемый орган, за который проводится голосование в разделе Голосование - Комитет в основном интерфейсе веб приложения.

Чтобы баллотироваться в комитет нужно сначала изменить статус аккаунта до сервисного (Настройки - Сервисный аккаунт), а затем в консоли cli_wallet, которую можно запустить в докере 

```docker run --rm -it hub.cwd.global/cwd-core:3.0 cli_wallet -s wss://cwd.global/ws/```

или собрать из исходников, выполнить следующие команды, в примерах будем использовать аккаунт *new-committee*:

инициализировать новый wallet и установить на него пароль, к примеру YOUR_PASSWOR:
```
set_password YOUR_PASSWOR
```

разблокировать wallet:
```
unlock YOUR_PASSWOR
```

Импортировать в него активный закрытый ключ вашего аккаунта, который можно найти на вкладке Права доступа - Действующие права доступа - Закрытый ключ:
```
import_key new-committee PRIVATE_KEY
```

Затем баллотироваться в комитет:
```
create_committee_member new-committee "" true
```

После этого новый член комитета появится во вкладке голосования, для того чтобы он стал активным вам нужно привлечь сообщество проголосовать за него на вкладке голосование-комитет и набрать столько голосов чтобы он вошёл в ТОП11 и стал активным.

Предложения о изменении параметров блокчейна может вносить каждый член комитета, но чтобы оно было активировано, нужно чтобы его поддержали большинство членов комитета.

## Внесение предложения об изменении параметров

Предложение об изменении параметров это транзакция, она содержит в себе все параметры блокчейна и их новые значения, например сейчас параметры блокчейна выглядят следующим образом (все дальнейшие команды выполняются в cli_wallet в разблокированном виде):

```
get_global_properties 

{
  "id": "2.0.0",
  "staking_parameters": {
    "poc_ref_01": 500,
    "poc_ref_02": 200,
    "poc_ref_03": 100,
    "poc_ref_04": 100,
    "poc_ref_05": 100,
    "poc_ref_06": 100,
    "poc_ref_07": 100,
    "poc_ref_08": 100,
    "poc_status_levels_00": 1,
    "poc_status_levels_01": 3,
    "poc_status_levels_02": 5,
    "poc_status_levels_03": 7,
    "poc_status_levels_04": 8,
    "poc_status_denominator_00": 2000,
    "poc_status_denominator_01": 8000,
    "poc_status_denominator_02": 10000,
    "poc_status_denominator_03": 10000,
    "poc_status_denominator_04": 10000,
    "poc_vote_duration": 86400,
    "poc_vote_interval_days": 90,
    "poc_min_votes": 160,
    "poc_filter_percent": 1000,
    "poc3_min_amount": 25000000,
    "poc6_min_amount": 25000000,
    "poc12_min_amount": 100000000
  },
  "gamezone_parameters": {
    "matrix_lasts_blocks": 60,
    "matrix_idle_blocks": 118380,
    "matrix_level_1_cells": 2,
    "matrix_level_2_cells": 2,
    "matrix_level_3_cells": 2,
    "matrix_level_4_cells": 2,
    "matrix_level_5_cells": 2,
    "matrix_level_6_cells": 2,
    "matrix_level_7_cells": 2,
    "matrix_level_8_cells": 2,
    "matrix_level_1_price": 4500000,
    "matrix_level_2_price": 8000000,
    "matrix_level_3_price": 14500000,
    "matrix_level_4_price": 26000000,
    "matrix_level_5_price": 46000000,
    "matrix_level_6_price": 83000000,
    "matrix_level_7_price": 150000000,
    "matrix_level_8_price": 270000000,
    "matrix_level_1_prize": 9000000,
    "matrix_level_2_prize": 16000000,
    "matrix_level_3_prize": 29000000,
    "matrix_level_4_prize": 52000000,
    "matrix_level_5_prize": 92000000,
    "matrix_level_6_prize": 166000000,
    "matrix_level_7_prize": 300000000,
    "matrix_level_8_prize": 540000000,
    "lottery_goods_total_participants": 5000,
    "lottery_goods_expiration": 2592000,
    "flipcoin_min_bet_amount": 1000
  },
  "greatrace_parameters": {
    "vote_duration": 86400,
    "min_team_status": 4,
    "min_team_volume": 0,
    "min_gr_bet": 500000,
    "min_votes": 50,
    "min_vote_last_rank": 7,
    "interval_1": 7,
    "interval_2": 21,
    "interval_3": 7,
    "interval_4": 21,
    "interval_5": 7,
    "interval_6": 21,
    "interval_7": 7,
    "interval_8": 7,
    "interval_9": 21,
    "interval_10": 7,
    "interval_11": 21,
    "interval_12": 7,
    "interval_13": 21,
    "interval_14": 7,
    "apostolos_reward": 100
  },
  "parameters": {
    "current_fees": {
      "parameters": [[
          0,{
            "fee": 1000000,
            "price_per_kbyte": 100000
          }
        ],[
          1,{
            "fee": 200000
          }
        ],[
          2,{
            "fee": 0
          }
        ],[
          3,{
            "fee": 200000
          }
        ],[
          4,{}
        ],[
          5,{
            "basic_fee": 500000,
            "premium_fee": 200000000,
            "price_per_kbyte": 100000
          }
        ],[
          6,{
            "fee": 200000,
            "price_per_kbyte": 100000
          }
        ],[
          7,{
            "fee": 300000
          }
        ],[
          8,{
            "membership_annual_fee": 20000000,
            "membership_lifetime_fee": 100000000
          }
        ],[
          9,{
            "fee": 50000000
          }
        ],[
          10,{
            "symbol3": "50000000000",
            "symbol4": "30000000000",
            "long_symbol": 2500000000,
            "price_per_kbyte": 10
          }
        ],[
          11,{
            "fee": 50000000,
            "price_per_kbyte": 10
          }
        ],[
          12,{
            "fee": 50000000
          }
        ],[
          13,{
            "fee": 50000000
          }
        ],[
          14,{
            "fee": 2000000,
            "price_per_kbyte": 100000
          }
        ],[
          15,{
            "fee": 2000000
          }
        ],[
          16,{
            "fee": 100000
          }
        ],[
          17,{
            "fee": 10000000
          }
        ],[
          18,{
            "fee": 50000000
          }
        ],[
          19,{
            "fee": 100000
          }
        ],[
          20,{
            "fee": 500000000
          }
        ],[
          21,{
            "fee": 2000000
          }
        ],[
          22,{
            "fee": 2000000,
            "price_per_kbyte": 10
          }
        ],[
          23,{
            "fee": 2000000,
            "price_per_kbyte": 10
          }
        ],[
          24,{
            "fee": 100000
          }
        ],[
          25,{
            "fee": 100000
          }
        ],[
          26,{
            "fee": 100000
          }
        ],[
          27,{
            "fee": 2000000,
            "price_per_kbyte": 10
          }
        ],[
          28,{
            "fee": 0
          }
        ],[
          29,{
            "fee": 500000000
          }
        ],[
          30,{
            "fee": 2000000
          }
        ],[
          31,{
            "fee": 100000
          }
        ],[
          32,{
            "fee": 100000
          }
        ],[
          33,{
            "fee": 200000
          }
        ],[
          34,{
            "fee": 500000000
          }
        ],[
          35,{
            "fee": 100000,
            "price_per_kbyte": 10
          }
        ],[
          36,{
            "fee": 100000
          }
        ],[
          37,{}
        ],[
          38,{
            "fee": 200000,
            "price_per_kbyte": 10
          }
        ],[
          39,{
            "fee": 500000,
            "price_per_output": 500000
          }
        ],[
          40,{
            "fee": 500000,
            "price_per_output": 500000
          }
        ],[
          41,{
            "fee": 500000
          }
        ],[
          42,{}
        ],[
          43,{
            "fee": 2000000
          }
        ],[
          44,{}
        ],[
          45,{
            "fee": 0
          }
        ],[
          46,{}
        ],[
          47,{
            "fee": 0
          }
        ],[
          48,{
            "fee": 0
          }
        ],[
          49,{
            "status_1_fee": 150000000,
            "status_2_fee": 750000000,
            "status_3_fee": 1500000000,
            "status_4_fee": 2500000000
          }
        ]
      ],
      "scale": 10000
    },
    "block_interval": 5,
    "maintenance_interval": 600,
    "maintenance_skip_slots": 3,
    "committee_proposal_review_period": 600,
    "maximum_transaction_size": 2048,
    "maximum_block_size": 2048000000,
    "maximum_time_until_expiration": 86400,
    "maximum_proposal_lifetime": 86400,
    "maximum_asset_whitelist_authorities": 10,
    "maximum_asset_feed_publishers": 10,
    "maximum_witness_count": 21,
    "maximum_committee_count": 11,
    "maximum_authority_membership": 10,
    "reserve_percent_of_fee": 2000,
    "network_percent_of_fee": 2000,
    "lifetime_referrer_percent_of_fee": 3000,
    "cashback_vesting_period_seconds": 31536000,
    "cashback_vesting_threshold": 10000000,
    "count_non_member_votes": true,
    "allow_non_member_whitelists": false,
    "witness_pay_per_block": 200000,
    "worker_budget_per_day": 1000000000,
    "max_predicate_opcode": 1,
    "fee_liquidation_threshold": 10000000,
    "accounts_per_fee_scale": 1000,
    "account_fee_scale_bitshifts": 4,
    "max_authority_depth": 2,
    "ref_01_percent_of_fee": 2000,
    "ref_02_percent_of_fee": 1000,
    "ref_03_percent_of_fee": 600,
    "ref_04_percent_of_fee": 400,
    "ref_05_percent_of_fee": 300,
    "ref_06_percent_of_fee": 200,
    "ref_07_percent_of_fee": 200,
    "ref_08_percent_of_fee": 300,
    "status_levels_00": 0,
    "status_levels_01": 3,
    "status_levels_02": 5,
    "status_levels_03": 7,
    "status_levels_04": 8,
    "denominator": true,
    "status_denominator_00": 0,
    "status_denominator_01": 7000,
    "status_denominator_02": 8000,
    "status_denominator_03": 9000,
    "status_denominator_04": 10000,
    "denominator_bonus_level": 4,
    "nv_levels": 30,
    "min_nv_status": 3,
    "ref_levels": 8,
    "compression_levels": 30,
    "compression": true,
    "cashback": false,
    "alllow_non_partner_register": true,
    "min_not_compressed": 3,
    "compression_limit": 0,
    "referral_statistic_seconds": 7776000,
    "root_account": "1.2.27",
    "nv_level_threshold_01": 1500000000,
    "nv_level_threshold_02": "3500000000",
    "nv_level_threshold_03": "10000000000",
    "nv_level_threshold_04": "25000000000",
    "nv_level_threshold_05": "45000000000",
    "nv_level_threshold_06": "70000000000",
    "nv_level_threshold_07": "150000000000",
    "nv_level_threshold_08": "300000000000",
    "status_threshold_01": 0,
    "status_threshold_02": 0,
    "status_threshold_03": 0,
    "status_threshold_04": 0,
    "nv_level_reward_01": 100,
    "nv_level_reward_02": 200,
    "nv_level_reward_03": 300,
    "nv_level_reward_04": 400,
    "nv_level_reward_05": 500,
    "nv_level_reward_06": 600,
    "nv_level_reward_07": 700,
    "nv_level_reward_08": 800,
    "extensions": []
  },
  "next_available_vote_id": 67,
  "active_committee_members": [
    "1.5.1",
    "1.5.2",
    "1.5.3",
    "1.5.4",
    "1.5.5",
    "1.5.6",
    "1.5.7",
    "1.5.8",
    "1.5.9",
    "1.5.10",
    "1.5.11"
  ],
  "active_witnesses": [
    "1.6.1",
    "1.6.23",
    "1.6.26",
    "1.6.27",
    "1.6.28",
    "1.6.35",
    "1.6.36",
    "1.6.37",
    "1.6.38",
    "1.6.44",
    "1.6.45"
  ]
}
```

Здесь нас интересует раздел **parameters** именно он будет изменён с помощью предложенной операции. Например сообщество решило изменить зарплату витнесов, так как при текущем курсе содержать сервера стало невозможно, создадим предложенную транзакцию от имени нашего нового члена комитета в которой будет изменён параметр witness_pay_per_block. В данный момент зарплата составляет 2 CWD за блок, поскольку в блокчейне все цифры храняться в целочисленном виде, а 1 CWD имеет 5 занков после запятой, то текущий параметр "witness_pay_per_block":200000. Увеличим его в 10 раз. 

Также можно изменять комиссию за проведение операций, она устанавливается в разделе "current_fees", это массив состоящий из обектов в которых первый элемент это порядковый номер операции в блокчейне (см. operations.hpp) а второй собственно сама комиссия.

В нашем примере мы изменим только зарплату витнеса, для этого нужно выполнить 4 команды

Инициализировать конструктор транзакций
```
begin_builder_transaction
```
Добавить операцию изменения параметров
```
add_operation_to_builder_transaction 0 [31,{"fee":{"amount":100000,"asset_id":"1.3.0"},"new_parameters":{"current_fees":{"parameters":[[0,{"fee":1000000,"price_per_kbyte":100000}],[1,{"fee":200000}],[2,{"fee":0}],[3,{"fee":200000}],[4,{}],[5,{"basic_fee":500000,"premium_fee":200000000,"price_per_kbyte":100000}],[6,{"fee":200000,"price_per_kbyte":100000}],[7,{"fee":300000}],[8,{"membership_annual_fee":20000000,"membership_lifetime_fee":100000000}],[9,{"fee":50000000}],[10,{"symbol3":"50000000000","symbol4":"30000000000","long_symbol":2500000000,"price_per_kbyte":10}],[11,{"fee":50000000,"price_per_kbyte":10}],[12,{"fee":50000000}],[13,{"fee":50000000}],[14,{"fee":2000000,"price_per_kbyte":100000}],[15,{"fee":2000000}],[16,{"fee":100000}],[17,{"fee":10000000}],[18,{"fee":50000000}],[19,{"fee":100000}],[20,{"fee":500000000}],[21,{"fee":2000000}],[22,{"fee":2000000,"price_per_kbyte":10}],[23,{"fee":2000000,"price_per_kbyte":10}],[24,{"fee":100000}],[25,{"fee":100000}],[26,{"fee":100000}],[27,{"fee":2000000,"price_per_kbyte":10}],[28,{"fee":0}],[29,{"fee":500000000}],[30,{"fee":2000000}],[31,{"fee":100000}],[32,{"fee":100000}],[33,{"fee":200000}],[34,{"fee":500000000}],[35,{"fee":100000,"price_per_kbyte":10}],[36,{"fee":100000}],[37,{}],[38,{"fee":200000,"price_per_kbyte":10}],[39,{"fee":500000,"price_per_output":500000}],[40,{"fee":500000,"price_per_output":500000}],[41,{"fee":500000}],[42,{}],[43,{"fee":2000000}],[44,{}],[45,{"fee":0}],[46,{}],[47,{"fee":0}],[48,{"fee":0}],[49,{"status_1_fee":150000000,"status_2_fee":750000000,"status_3_fee":1500000000,"status_4_fee":2500000000}]],"scale":10000},"block_interval":5,"maintenance_interval":600,"maintenance_skip_slots":3,"committee_proposal_review_period":600,"maximum_transaction_size":2048,"maximum_block_size":2048000000,"maximum_time_until_expiration":86400,"maximum_proposal_lifetime":86400,"maximum_asset_whitelist_authorities":10,"maximum_asset_feed_publishers":10,"maximum_witness_count":21,"maximum_committee_count":11,"maximum_authority_membership":10,"reserve_percent_of_fee":2000,"network_percent_of_fee":2000,"lifetime_referrer_percent_of_fee":3000,"cashback_vesting_period_seconds":31536000,"cashback_vesting_threshold":10000000,"count_non_member_votes":true,"allow_non_member_whitelists":false,"witness_pay_per_block":2000000,"worker_budget_per_day":1000000000,"max_predicate_opcode":1,"fee_liquidation_threshold":10000000,"accounts_per_fee_scale":1000,"account_fee_scale_bitshifts":4,"max_authority_depth":2,"ref_01_percent_of_fee":2000,"ref_02_percent_of_fee":1000,"ref_03_percent_of_fee":600,"ref_04_percent_of_fee":400,"ref_05_percent_of_fee":300,"ref_06_percent_of_fee":200,"ref_07_percent_of_fee":200,"ref_08_percent_of_fee":300,"status_levels_00":0,"status_levels_01":3,"status_levels_02":5,"status_levels_03":7,"status_levels_04":8,"denominator":true,"status_denominator_00":0,"status_denominator_01":7000,"status_denominator_02":8000,"status_denominator_03":9000,"status_denominator_04":10000,"denominator_bonus_level":4,"nv_levels":30,"min_nv_status":3,"ref_levels":8,"compression_levels":30,"compression":true,"cashback":false,"alllow_non_partner_register":true,"min_not_compressed":3,"compression_limit":0,"referral_statistic_seconds":7776000,"root_account":"1.2.27","nv_level_threshold_01":1500000000,"nv_level_threshold_02":"3500000000","nv_level_threshold_03":"10000000000","nv_level_threshold_04":"25000000000","nv_level_threshold_05":"45000000000","nv_level_threshold_06":"70000000000","nv_level_threshold_07":"150000000000","nv_level_threshold_08":"300000000000","status_threshold_01":0,"status_threshold_02":0,"status_threshold_03":0,"status_threshold_04":0,"nv_level_reward_01":100,"nv_level_reward_02":200,"nv_level_reward_03":300,"nv_level_reward_04":400,"nv_level_reward_05":500,"nv_level_reward_06":600,"nv_level_reward_07":700,"nv_level_reward_08":800,"extenions":[]}}]
```

Предложим новые параметры на утверждение комитету (на данный момент на утверждение отводится 600 секунд, если в течение этого времени транзакция не будет утверждена, она отменится автоматически), третий параметр в виде штампа времени должен быть указан в UTC и при этом показывать на 15 минут больше чем текущее время.

```
propose_builder_transaction2 0 init0 "2021-10-01T18:10:00" 600 true
```

Очистим конструктор транзакций
```
remove_builder_transaction 0
```

Теперь нужно получить ID предложения, чтобы другие члены комитета смогли его утвердить:
```
get_account_history new-committee 1
```

В ответ получим историю операций в которой будет поле result: 1.10.ХХХ

1.10.ХХХ - это и есть ID предложения.

## Утверждение предложения о внесении новых параметров

Теперь тот член комитета который внёс предложение должен сообщить его ID всем остальным членам комитета, и они должны за него проголосовать, если большинство проголосует то новые параметры будут активированы в следующий интервал обслуживания (раз в 10 минут):

Чтобы принять предложение каждый из членов комитета долен войти в свой cli_wallet и разблокировать его, импортировать ключ если этого не было сделано ранее, а затем провести транзакцию утверждения, например для члена комитета committee1 транзакция будет такая:
```
approve_proposal committee1 "1.10.XXX" {"active_approvals_to_add" : ["committee1"]} true
```

Как только это действие совершат более половины комитета - параметры перейдут в режим ожидания и активируются в следующий период обслуживания. И с этого момента блокчейн будет использовать новые значения при проведении операций.

