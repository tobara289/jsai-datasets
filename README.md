## Note

jsai_base/jsai2020.json についてのみ和名により組織名の表現揺れを統一した下記キーを追加

+ org_jp : 組織名
+ authors_org_jp : 組織名に紐づく著者名

J-STAGE の予稿集ベースのファイル作成



## Dataset

### Proceeding base
このデータセットは J-STAGE の予稿集を json 形式へ変換したものです。

```
{
	"paper_num": {
		"url": String Type,
 		"title": String Type,
 		"keywords": List Type,
 		"co-author": List Type,
 		"org": Dict Type,
 		"author_org": { 
                	"org_num": List Type,
 		"abstract": None
	}
}
```


### Web page base
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
+ section_num : 区分番号
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


## Example
```
{
	'[999-AA-999-01]' {
		'url': 'https://***',
 		'category': '〇〇〇',
 		'sub_category': {'1': '〇〇〇', '2': '▲▲▲'},
 		'section_num': '[999-AA-999]',
 		'section_title': '×××',
 		'schedule_num': 999,
 		'like_num': 999,
 		'comment_num': 999,
 		'keywords': ['●●●', '■■■'],
 		'title': '◎◎◎',
 		'org': {'1': 'Univ. of □□□', '2': 'Univ. of △△△'},
 		'co-author': ['Bob'],
 		'author': 'Alice',
 		'authors_org': {'1': ['Alice'], '2': ['Bob']}
	}
}
```
## Organization Name
組織名の表現揺れの解決ロジック  
ただし，明らかな間違いについては修正する  
(例)  
産業総合技術研究所 -> 産業技術総合研究所  
應義塾大学 -> 慶應義塾大学  
慶応大学 -> 慶應義塾大学  

### Company
1. 前株および後株それぞれ省略せずに「株式会社」を記載した表記統一
+ （株）〇〇 -> 株式会社〇〇
+ 株〇〇 -> 株式会社〇〇
+ 〇〇（株）-> 株式会社〇〇
+ 〇〇株 -> 〇〇株式会社

2. 研究所については，企業内の1部門の場合は会社名で統一し，子会社/グループ会社の場合別表記
(会社の一組織)
+ 〇〇会社〇〇コミュニケーション研究所 -> 〇〇株式会社
(子会社/グループ会社)
+ 〇〇コミュニケーション研究所 -> □□株式会社

3. 英数字は半角表記に統一する
+ ＡＢＣ株式会社 -> ABC株式会社 

### Academy
1. 学科や学類などを削除し，「学校法人」を除いた表記に統一
+ 〇〇大学〇〇学科 -> 〇〇大学
+ 〇〇大 -> 〇〇大学

2. 高等専門学校は「独立行政法人国立高等専門学校機構」を除いた表記
+ 独立行政法人国立高等専門学校機構〇〇高等専門学校 -> 〇〇高等専門学校

3. 略字は元の字に戻す
+ 慶応義塾大学 -> 慶應義塾大学

### Administration
1. 「国立研究開発法人」を除外した表記に統一
+ 国立研究開発法人〇〇機構 -> 〇〇機構
+ 〇〇研 -> 〇〇研究所

2. 別法人でなければ，部門を除外する
+ 〇〇研AI研究グループ -> 〇〇研究所
