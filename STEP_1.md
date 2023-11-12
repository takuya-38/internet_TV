# STEP_1

# テーブル一覧

## channels

| カラム名     | データ型     | NULL | キー    | 初期値 | AUTO INCREMENT |
| ------------ | ------------ | ---- | ------- | ------ | -------------- |
| channel_id   | int          |      | PRIMARY |        | YES            |
| channel_name | varchar(100) |      |         |        |                |

<br>

## program_schedule

| カラム名          | データ型   | NULL | キー    | 初期値 | AUTO INCREMENT |     |
| ----------------- | ---------- | ---- | ------- | ------ | -------------- | --- |
| schedule_id       | int        |      | PRIMARY |        | YES            |     |
| channel_id        | int        |      | FOREIGN |        |                |     |
| program_detail_id | int        |      | FOREIGN |        |                |     |
| start_time        | datetime   |      |         |        |                |     |
| end_time          | datetime   |      |         |        |                |     |
| watch_count       | bigint(20) |      |         | 0      |                |     |

- 外部キー制約：channel_id に対して、channels テーブルの channel_id カラムから設定
- 外部キー制約：program_detail_id に対して、program_details テーブルの program_detail_id カラムから設定

<br>

## program_details

| カラム名          | データ型     | NULL | キー    | 初期値 | AUTO INCREMENT |
| ----------------- | ------------ | ---- | ------- | ------ | -------------- |
| program_detail_id | int          |      | PRIMARY |        |                |
| program_id        | int          |      | INDEX   |        |                |
| series_id         | int          |      | INDEX   | 0      |                |
| episode_id        | int          |      | INDEX   | 0      |                |
| episode_title     | varchar(100) |      |         | -      |                |
| episode_info      | varchar(400) |      |         | -      |                |
| duration          | int          |      |         |        |                |
| release_date      | date         |      |         |        |                |

- 外部キー制約：program_id に対して、programs テーブルの program_id カラムから設定
- ユニークキー制約：program_id, series_id, episode_id カラムに対して設定

<br>

## programs

| カラム名      | データ型     | NULL | キー    | 初期値 | AUTO INCREMENT |
| ------------- | ------------ | ---- | ------- | ------ | -------------- |
| program_id    | int          |      | PRIMARY |        | YES            |
| program_title | varchar(100) |      |         |        |                |
| program_info  | varchar(400) |      |         |        |                |

<br>

## program_genres

| カラム名         | データ型 | NULL | キー    | 初期値 | AUTO INCREMENT |
| ---------------- | -------- | ---- | ------- | ------ | -------------- |
| program_genre_id | int      |      | PRIMARY |        | YES            |
| program_id       | int      |      | FOREIGN |        |                |
| genre_id         | int      |      | FOREIGN |        |                |

- 外部キー制約：genre_id に対して、genres テーブルの genre_id カラムから設定
- 外部キー制約：program_id に対して、programs テーブルの program_id カラムから設定

<br>

## genres

| カラム名   | データ型     | NULL | キー    | 初期値 | AUTO INCREMENT |
| ---------- | ------------ | ---- | ------- | ------ | -------------- |
| genre_id   | int          |      | PRIMARY |        | YES            |
| genre_name | varchar(100) |      |         |        |                |
