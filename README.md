# 数字影像素材与播出资料

以下台账为合成数据，不涉及真实访客、供应商或展馆。CSV 采用 UTF-8，首行为字段名，空字段代表源资料未给出。标识仅在字段明示的实体范围内使用。`data/agreements.json` 是当期业务方提供的运营资料，`data/formats.json` 记录文件列顺序和确定的外键引用。

- `data/sources.csv` 记录母片身份、用以划分相似镜头的素材族和媒体长度。列为 `work`、`family`、`label`、`seconds`、`partition`。
- `data/fingerprint.csv` 记录每个母片的原向和镜像指纹。列为 `work`、`second`、`native`、`mirrored`。
- `data/edits.csv` 记录收到的成片元数据，不声明已用母片。列为 `edit`、`title`、`seconds`、`transform`、`possible_rates`、`received_day`。
- `data/edit_fingerprint.csv` 记录成片可见摘要。列为 `edit`、`second`、`sample`、`noise_band`。
- `data/review.csv` 记录审片员在特定范围确认或排除的关系，半开区间。列为 `review`、`edit`、`start`、`end`、`work`、`work_start`、`work_end`、`judgment`、`revision_day`。
- `data/rights.csv` 记录权利片段、使用期、允许的馆与计费单位。列为 `right`、`work`、`first`、`last`、`holder`、`venues`、`day_from`、`day_to`、`cents`、`basis`、`status`。
- `data/shows.csv` 记录场次和计划成片的对应。列为 `show`、`day`、`venue`、`screens`、`scheduled_edit`、`edition`。
- `data/display.csv` 记录播放器从成片位置 first 播到 last 的真实屏和时钟记录。列为 `event`、`show`、`screen`、`edit`、`first`、`last`、`wall_first`、`wall_last`、`observed`、`revision_day`。
- `data/journal.csv` 记录实际对账或财务状态，first/last 为母片区间。列为 `entry`、`show`、`work`、`first`、`last`、`right`、`cents`、`state`、`received_day`。

使用 Python 3.11，无第三方依赖。用 `python3 -m unittest discover -s tests -v` 核对文件的可读性、列结构和确定引用，源文件保持只读。
