## Dataset
このデータセットは人工知能学会全国大会の大会プログラムを json 形式へ変換したものである。

```
{
	セッション番号: {
		"url": String Type,
		"category": String Type,
		"sub_category": Dict Type,
		"section_num": String Type,
		"section_title": String Type,
		"schedule_num": Int Type,
		"like_num": Int Type,
		"comment_num": Int Type,
		"keywords": List Type,
		"title":  String Type,
		"org":  Dict Type,
		"co-author": List Type,
		"author": String Type,
		"authors_org": {
			組織番号 : List Type
		}
	}
}
```
