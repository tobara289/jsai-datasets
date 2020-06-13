## Dataset
このデータセットは人工知能学会全国大会の大会プログラムを json 形式へ変換したものです。

```
{
	"paper_num": {
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
			"org_num" : List Type
		}
	}
}
```

+ paper_num : 発表番号
+ section_num : セッション番号
+ url         : 発表内容参照URL
+ category    : 発表種別
+ sub_category : 発表区分リスト
+ section_title : 発表中区分
+ schedule_num : 聴講予定者
+ like_num : 評価数
+ comment_num : コメント数
+ keywords : キーワード
+ title : 発表タイトル
+ org : 組織名
+ co-author : 共著者
+ author : 筆頭著者
+ authors_org : 所属組織
