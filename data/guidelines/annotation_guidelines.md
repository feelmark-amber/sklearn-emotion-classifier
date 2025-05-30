# 文学作品に対する読者の感情記述テキスト分析のためのアノテーションガイドライン (バイナリ・マルチラベル分類)

**バージョン:** 2.0
**最終更新日:** 2025年4月17日

## 1. はじめに

### 1.1. ガイドラインの目的
本ガイドラインは、文学作品（小説、詩、エッセイなど）に対する読者の感情的な反応を記述したテキストデータを分析し、Alan Cowen と Dacher Keltner が2017年の研究で提案した27の感情カテゴリー [1, 2, 3, 4, 5] に基づいて分類するためのアノテーション作業の基準と手順を定義します。

### 1.2. 重要性
本アノテーション作業の目的は、読者の感情記述テキストから表現されている感情を特定し、高品質な教師データセットを作成することです。このデータセットは、文学に対する読者の多様で微妙な感情反応を理解・分析するAIモデルの開発に不可欠な基盤となります。したがって、本ガイドラインに従い、一貫性と精度の高いアノテーションを実施することが極めて重要です。

### 1.3. 対象者
本ガイドラインは、アノテーション作業を担当するすべてのアノテーターを対象としています。

### 1.4. 感情モデルに関する注記
*   **モデルの由来:** 本ガイドラインで採用する27感情カテゴリーモデルは、主に短いビデオクリップに対する人々の自己申告反応に基づいて構築されました [6, 1, 2, 3, 4, 7, 5]。文学作品への反応という、より複雑で内省的なテキストデータに適用する際には、文脈を慎重に考慮する必要があります。
*   **感情の勾配性:** 研究では、これらの感情カテゴリー間に明確な境界があるわけではなく、むしろ滑らかな勾配（連続的な変化）が存在することが示唆されています（例：「不安」から「恐れ」、「恐れ」から「Horror」へ） [6, 1, 2, 3, 5]。本タスクはバイナリ（有無）分類ですが、この感情の連続性を念頭に置き、カテゴリー間の境界事例の判断には特に注意が必要です。

## 2. タスク概要

### 2.1. アノテーターの役割
アノテーターは、提供された各「ユーザーの感情記述テキスト」を注意深く読み、そのテキストに表現されている**読者自身の感情**を特定し、セクション4で定義された27の感情カテゴリーの中から該当するものを**すべて**選択します。

### 2.2. 入力データ
文学作品に対する読者の感想、レビュー、コメントなどの日本語テキスト。

### 2.3. 出力データ
各テキストに対して、該当すると判断された感情カテゴリーのラベルリスト（セクション9参照）。

### 2.4. アノテーション方式
**バイナリ・マルチラベル分類:**
各テキストについて、27の感情カテゴリーそれぞれに対し、その感情がテキスト中に**明確に表現されているか（=1）**、**いないか（=0）**を判断します。一つのテキストに複数の感情が該当する場合、該当するすべての感情を選択します。スコア付け（例: 0.1〜1.0）は行いません。

## 3. 基本原則・一般的な指示

*   **注意深い読解:** 各テキストを完全に理解するために、注意深く読んでください。単語の意味だけでなく、文脈、ニュアンス、比喩、全体的なトーンを考慮してください。
*   **文脈の考慮:** 感情は文学作品に対する反応として表現されています。作品のどの側面（プロット、キャラクター、文体、テーマ、結末など）が感情を引き起こしている可能性があるかを考慮して解釈してください。
*   **読者自身の感情への焦点:** アノテーションは、テキストの書き手（読者）が表明している**自身の感情**に焦点を当ててください。作中の登場人物の感情描写や、書き手が他者の感情について推測している記述は対象外です（詳細はセクション7.3参照）。
*   **テキストに基づく客観的判断:** あなた自身の個人的な感情や意見ではなく、テキストに書かれている内容に基づいて客観的に判断してください。「この読者はこう感じているはずだ」と推測するのではなく、「テキストにはこのように書かれている」という証拠に基づいて判断します。
*   **「明確な根拠」の原則:** ある感情が存在する（ラベル=1）と判断するには、テキスト中にその感情を示す**明確な表現や根拠**が必要です。曖昧な表現や、複数の解釈が可能で確信が持てない場合は、「存在しない（ラベル=0）」と判断してください（詳細はセクション7.2参照）。
*   **一貫性の重要性:** ガイドライン全体を通して一貫した基準で判断することが、データセットの品質にとって非常に重要です。判断に迷った場合は、本ガイドラインの定義や具体例、類似カテゴリーとの区別を再確認してください。

## 4. 感情カテゴリーリスト

アノテーションには、Cowen & Keltner (2017) の研究 [1, 2, 3, 4, 5] に基づく以下の27の感情カテゴリーを使用します。

**重要:**
*   **英語名が正:** 日本語訳はあくまで参考情報です。感情の概念は文化や言語によってニュアンスが異なる可能性があるため [8, 9]、アノテーションの最終的な判断は**英語のカテゴリー名とその定義（セクション5）**に基づいて行ってください。
*   **訳語の選択:** 日本語訳は、学術的な整合性 [10] や一般的な用法を考慮して選択・修正されていますが、依然として解釈の幅が存在する可能性があります。特に注意が必要な語には注釈を加えています。

| # | English Name | 日本語参照訳 (参考) | 注釈 |
|---|------------------------|--------------------------|----------------------------------------------------------------------|
| 1 | Admiration | 敬服 (Keifuku) | [11, 7] |
| 2 | Adoration | 崇拝 (Sūhai) | [11, 7] |
| 3 | Aesthetic Appreciation | 美的感動 (Biteki Kandō) | [10] (一般記事の「称賛」[11, 7] は不適切) |
| 4 | Amusement | 愉快 (Yukai) | [10] (「娯楽」[11, 7] より感情表現として適切) |
| 5 | Anger | 怒り (Ikari) | (一般的) |
| 6 | Anxiety | 焦慮 (Shōryo) | [11, 7] |
| 7 | Awe | 畏敬 (Ikei) | [11, 7] (文化的含意に注意 [12, 13]) |
| 8 | Awkwardness | 当惑 (Tōwaku) | [11, 7] (気まずさ、居心地の悪さ) |
| 9 | Boredom | 退屈 (Taikutsu) | (「飽きる」[11, 7] より状態を示す語として) |
| 10| Calmness | 冷静 (Reisei) / 穏やかさ | [11, 7] |
| 11| Confusion | 困惑 (Konwaku) | [11, 7] (混乱) |
| 12| Craving | 渇望 (Katsubō) | [11, 7] |
| 13| Disgust | 嫌悪 (Ken'o) | [11, 7] |
| 14| Empathic Pain | 共感による痛み (Kyōkan niyoru Itami) | [11, 7] (同情とは区別 [4, 14]) |
| 15| Entrancement | 夢中 (Muchū) | [11, 7] (没頭、恍惚) |
| 16| Excitement | 興奮 (Kōfun) | [11, 7] (ワクワク感) |
| 17| Fear | 恐怖 (Kyōfu) | [10] (「恐れ」[11, 7] より強いニュアンスの場合も含む) |
| 18| Horror | 戦慄 (Senritsu) | (「痛恨」[11, 7] は不適切。極度の恐怖＋嫌悪) |
| 19| Interest | 興味 (Kyōmi) | [10] (「面白さ」[11, 7] はAmusementと混同の可能性) |
| 20| Joy | 喜び (Yorokobi) | [10] |
| 21| Nostalgia | 懐旧 (Kaikyū) | [11, 7] (郷愁) |
| 22| Relief | 安堵 (Ando) | [4, 14] |
| 23| Romance | ロマンス (Romansu) | [11, 7] (ときめき) |
| 24| Sadness | 悲しみ (Kanashimi) | [10] |
| 25| Satisfaction | 満足 (Manzoku) | [11, 7] |
| 26| Sexual Desire | 性的欲求 (Seiteki Yokkyū) | [11, 7] |
| 27| Surprise | 驚き (Odoroki) | (一般的) |

*(注: 上記リストは Cowen & Keltner (2017) [1, 3, 4] で特定された27カテゴリーです。研究によっては初期リスト(34カテゴリー) [1, 4, 15] や、他の研究者のリスト [16, 17, 18] に言及している場合がありますが、本タスクでは上記27カテゴリーのみを使用します。)*

## 5. 各感情カテゴリーの定義と判断基準 (バイナリ判定用)

ここでは、27の各感情カテゴリーについて、定義、ラベル=1（存在する）と判断する基準、具体例（ラベル=1/0）、類似カテゴリーとの区別を記述します。**「明確な根拠」**がある場合にのみラベル=1と判断してください。

---

**(1) Admiration (敬服)**
*   **定義:** 作者の技術、登場人物の能力や道徳性、作品の構成やテーマの深さなど、人や作品の優れた点に対する尊敬、敬意、高い評価。「すごい」「見事だ」「感服する」といった知的な感嘆。
*   **判断基準 (ラベル=1):** テキストが、作品や登場人物、作者の**特定の質、能力、技術、道徳性**に対して、明確に**尊敬、敬意、賞賛、感嘆**の念を示している場合。
*   **具体例 (ラベル=1):**
    *   「これほど緻密な伏線を回収する構成力には脱帽です。」
    *   「どんな逆境でも信念を貫く主人公の強さに心から敬服した。」
    *   「作者の人間洞察の深さにはただただ感嘆するばかりだ。」
*   **具体例 (ラベル=0):**
    *   「全体的にとても面白い小説だった。」（→Joy, Satisfactionなど）
    *   「情景描写が本当に美しくて引き込まれた。」（→Aesthetic Appreciation）
    *   「このキャラクターが大好き！」（→Adoration）
*   **類似カテゴリーとの区別:**
    *   *Aesthetic Appreciation:* 美しさや芸術性への感覚的な感動ではなく、質や能力への知的な評価。
    *   *Awe:* スケールや深遠さへの圧倒感ではなく、具体的な優れた点への尊敬。
    *   *Adoration:* 熱烈な愛着や傾倒ではなく、尊敬や評価。

**(2) Adoration (崇拝)**
*   **定義:** 特定の登場人物や作者、あるいは作品世界全体に対する、非常に強い愛情、献身、時には盲目的なまでの好意。「大好き」「推せる」「たまらない」「愛してる」といった熱烈な感情。
*   **判断基準 (ラベル=1):** テキストが、特定の対象（キャラ、作者、作品世界）に対して、個人的で**熱烈な愛情、愛着、献身、強い好意**を明確に表現している場合。しばしば熱狂的な言葉遣いを伴う。
*   **具体例 (ラベル=1):**
    *   「〇〇（キャラ名）が好きすぎて現実が見えない！彼のためなら何でもできる！」
    *   「この作家さんの作品は私の人生のバイブル。新作が出るたびに崇拝の念が増す。」
    *   「この作品の世界観がたまらなく好き。ずっと浸っていたい。」
*   **具体例 (ラベル=0):**
    *   「主人公の生き様には感銘を受けた。」（→Admiration）
    *   「二人の関係が微笑ましくて好き。」（→Joy, Romance）
    *   「読んでいてとても楽しかった。」（→Joy）
*   **類似カテゴリーとの区別:**
    *   *Admiration:* 尊敬や評価ではなく、熱烈な「愛着」「傾倒」。
    *   *Romance:* 恋愛的なときめきだけでなく、より広範で強い愛着や献身。
    *   *Joy:* 一般的な喜びよりも、特定の対象への強い個人的な愛着。

**(3) Aesthetic Appreciation (美的感動)**
*   **定義:** 文章の美しさ、情景描写の鮮やかさ、比喩表現の巧みさ、構成美、装丁や挿絵を含めた作品全体の芸術性など、感覚的・美的な側面に対する喜びや感動。「美しい」「きれい」「うっとりする」「芸術的だ」という感覚。
*   **判断基準 (ラベル=1):** テキストが、作品の**美的側面（文体、描写、構成、デザインなど）**に対して、明確に**美しさ、芸術性、感覚的な心地よさ**を感じていることを表現している場合。
*   **具体例 (ラベル=1):**
    *   「詩的で流れるような文章にうっとりした。一文一文が芸術のよう。」
    *   「夕暮れの描写が目に浮かぶようで、その美しさに息をのんだ。」
    *   「この小説は構成自体が美しく、完璧なバランスを感じる。」
*   **具体例 (ラベル=0):**
    *   「作者のプロット構築能力は素晴らしい。」（→Admiration）
    *   「壮大な世界観に圧倒された。」（→Awe）
    *   「とても感動的な物語だった。」（→Joy, Sadnessなど文脈による）
*   **類似カテゴリーとの区別:**
    *   *Admiration:* 技術や質への知的な評価ではなく、美しさへの感覚的な反応。
    *   *Awe:* スケールや深遠さへの圧倒感ではなく、主に美しさや芸術性への感動。
    *   *Joy:* 一般的な喜びよりも、美的側面への特定の感動。
    *   *Calmness:* 穏やかさだけでなく、美しさに対するポジティブな感動を伴う。

**(4) Amusement (愉快)**
*   **定義:** ユーモア、機知に富んだ会話、コミカルな状況、皮肉、登場人物の面白い行動などによって引き起こされる「面白い（おかしい）」「笑える」「楽しい（軽快な）」という感情。ポジティブで軽快な感覚。
*   **判断基準 (ラベル=1):** テキストが、作品の**ユーモラスな要素、コミカルな点、機知**に対して、明確に**面白さ、おかしさ、笑い、軽快な楽しさ**を感じていることを表現している場合。「笑った」「吹き出した」「面白い（funny）」などの表現が手がかり。
*   **具体例 (ラベル=1):**
    *   「登場人物たちの間の抜けた会話が面白すぎて、声を出して笑ってしまった。」
    *   「シニカルなユーモアが随所に散りばめられていて、読んでいてとても愉快だった。」
    *   「主人公のドジっぷりがおかしくて、憎めない。」
*   **具体例 (ラベル=0):**
    *   「ストーリー展開が興味深くて面白かった。」（→Interest）
    *   「読んでいてとても楽しかった。」（→Joy, Excitementなど文脈による）
    *   「皮肉な結末に考えさせられた。」（→Interest, Confusionなど）
*   **類似カテゴリーとの区別:**
    *   *Joy:* より広範な喜びや幸福感ではなく、主に「笑い」「ユーモア」「軽快さ」に関連。
    *   *Excitement:* スリルや期待感ではなく、面白さや滑稽さ。
    *   *Interest:* 知的な好奇心ではなく、面白さや笑い。

**(5) Anger (怒り)**
*   **定義:** 作中の不正義な出来事、登場人物の許せない行動、理不尽な展開、あるいは作者や作品自体（期待外れ、不快な内容など）に対する不満、憤り、敵意。「腹が立つ」「許せない」「ムカつく」「ふざけるな」という感情。
*   **判断基準 (ラベル=1):** テキストが、作品内の出来事、登場人物、作者、または作品全体に対して、明確に**不満、憤り、敵意、攻撃的な非難**を表現している場合。
*   **具体例 (ラベル=1):**
    *   「あの登場人物の裏切り行為には本当に腹が立った。絶対に許せない。」
    *   「こんな理不尽な結末なんて、読者を馬鹿にしているとしか思えない。怒りを感じる。」
    *   「差別的な描写が多く、読んでいて不快だったし、作者に対して怒りを覚えた。」
*   **具体例 (ラベル=0):**
    *   「彼の行動にはがっかりした。」（→Disappointment (本リスト外だが近い) / Sadness）
    *   「読んでいて気分が悪くなった。」（→Disgust）
    *   「結末には納得がいかなかった。」（→Satisfaction (低い), Confusion）
*   **類似カテゴリーとの区別:**
    *   *Disgust:* 嫌悪感や不快感だけでなく、より強い「憤り」「攻撃性」を伴う。
    *   *Sadness:* 悲しみや失望ではなく、不正や裏切りに対する怒り。
    *   *Boredom:* 退屈さではなく、積極的な不満や憤り。

**(6) Anxiety (焦慮)**
*   **定義:** 物語の今後の展開、登場人物の安否、危機的な状況、未解決の謎などに対する心配、懸念、落ち着かない気持ち。「どうなるんだろう」「心配だ」「ハラハラする」「無事でいてほしい」という未来へのネガティブな予測や落ち着かなさ。
*   **判断基準 (ラベル=1):** テキストが、物語の**未来の展開や結果**に対して、明確に**心配、懸念、落ち着かなさ、不安感**を表現している場合。「ハラハラする」「気がかり」「無事を祈る」などの表現が手がかり。
*   **具体例 (ラベル=1):**
    *   「主人公が敵に捕まってしまい、これからどうなるのか心配でページをめくる手が震えた。」
    *   「この不穏な伏線、絶対悪いことが起こる前触れだ…不安で仕方ない。」
    *   「結末がどうなるか気になって、夜も眠れないほど落ち着かない。」
*   **具体例 (ラベル=0):**
    *   「敵が登場するシーンは怖かった。」（→Fear）
    *   「次の展開が楽しみでワクワクする。」（→Excitement）
    *   「謎が多くて混乱した。」（→Confusion）
*   **類似カテゴリーとの区別:**
    *   *Fear:* 直接的で具体的な脅威への反応ではなく、未来の不確実な脅威や結果への「心配」。
    *   *Excitement:* ポジティブな期待感ではなく、ネガティブな結果への懸念。
    *   *Interest:* 知りたいという好奇心だけでなく、心配や落ち着かなさを伴う。

**(7) Awe (畏敬)**
*   **定義:** 作品の壮大なスケール（時間的、空間的）、テーマの深遠さ、自然や宇宙の描写、超越的な出来事、人間の偉業などに対して感じる、畏れや敬意を伴う圧倒的な感動。「すごい（桁違いに）」「言葉が出ない」「ちっぽけに感じる」「神々しい」という感覚。自己の小ささを感じる体験。
*   **判断基準 (ラベル=1):** テキストが、作品の**壮大さ、深遠さ、超越性**に対して、明確に**圧倒される感覚、畏れ、敬意、自己の相対的な小ささ**を感じていることを表現している場合。
*   **具体例 (ラベル=1):**
    *   「宇宙の広大さを描いた描写に、ただただ圧倒され、自分の存在の小ささを感じた。」
    *   「何世代にもわたる壮大な物語のスケールに畏敬の念を抱いた。」
    *   「自然の驚異に対する描写が神々しく、言葉を失うほどだった。」
*   **具体例 (ラベル=0):**
    *   「作者の構成力は見事だ。」（→Admiration）
    *   「風景描写がとても美しかった。」（→Aesthetic Appreciation）
    *   「予期せぬ展開に驚いた。」（→Surprise）
*   **類似カテゴリーとの区別:**
    *   *Admiration:* 具体的な質や能力への尊敬ではなく、スケールや深遠さへの「圧倒される」感覚。
    *   *Aesthetic Appreciation:* 美しさへの感動だけでなく、壮大さや深遠さに対する畏れや圧倒感を伴う。
    *   *Fear:* 脅威への反応ではなく、偉大さや壮大さに対する畏れ。
    *   *Surprise:* 単なる予期せぬ出来事ではなく、スケールや意味合いにおいて圧倒されるような驚き。
    *   *(注意)* 日本語の「畏敬」は西洋の'Awe'と完全に一致しない可能性あり [12, 13]。英語定義を優先。

**(8) Awkwardness (当惑)**
*   **定義:** 作中の登場人物間の気まずい会話や状況、社会的な失敗、共感性羞恥（他人の失敗を自分のことのように恥ずかしいと感じる）などを読んで、読者自身が感じる居心地の悪さ、落ち着かなさ、気まずさ。「うわぁ…」「見てられない」「こっちが恥ずかしい」「気まずい」という感覚。
*   **判断基準 (ラベル=1):** テキストが、作中の**社会的な気まずさ、失敗、ぎこちない状況**に対して、読者自身が明確に**居心地の悪さ、落ち着かなさ、共感性羞恥**を感じていることを表現している場合。
*   **具体例 (ラベル=1):**
    *   「二人の会話が気まずすぎて、読んでるこっちまで冷や汗が出た。」
    *   「主人公がパーティで大失敗するシーンは、痛々しくて見ていられなかった。うわぁって声が出た。」
    *   「あの場の空気の読めない発言、本当に気まずかった…。」
*   **具体例 (ラベル=0):**
    *   「主人公の苦境に胸が痛んだ。」（→Empathetic Pain）
    *   「彼の行動にはイライラした。」（→Anger）
    *   「状況がよく理解できず困惑した。」（→Confusion）
*   **類似カテゴリーとの区別:**
    *   *Empathetic Pain:* 相手の苦痛への共感ではなく、社会的な場面での「居心地の悪さ」。
    *   *Anxiety:* 未来への不安ではなく、現在進行形の気まずさ。
    *   *Confusion:* 理解できないことによる当惑ではなく、社会的な状況に対する気まずさ。

**(9) Boredom (退屈)**
*   **定義:** 物語の単調さ、展開の遅さ、内容の陳腐さ、興味を引かれないテーマ、冗長な描写などによって感じる、刺激不足、関心のなさ、時間の長さ。「つまらない」「退屈だ」「眠くなった」「早く終わらないかな」というネガティブな低覚醒状態。
*   **判断基準 (ラベル=1):** テキストが、作品の**単調さ、刺激のなさ、興味の欠如**に対して、明確に**退屈さ、つまらなさ、関心のなさ**を感じていることを表現している場合。
*   **具体例 (ラベル=1):**
    *   「ストーリーが単調で、正直言って途中からかなり退屈だった。」
    *   「風景描写が延々と続いて、さすがに飽きてしまった。」
    *   「特に何も起こらず、刺激のないまま終わってしまい、退屈な読書体験だった。」
*   **具体例 (ラベル=0):**
    *   「内容が難しくて理解できなかった。」（→Confusion）
    *   「期待外れでがっかりした。」（→Sadness, Anger）
    *   「静かで穏やかな話だった。」（→Calmness）
*   **類似カテゴリーとの区別:**
    *   *Sadness/Anger:* 悲しみや怒りといった強い感情ではなく、刺激や興味の「欠如」。
    *   *Confusion:* 理解できないことによる当惑ではなく、内容への関心のなさ。
    *   *Calmness:* ポジティブな平穏さではなく、ネガティブな刺激不足。

**(10) Calmness (冷静 / 穏やかさ)**
*   **定義:** 心地よい雰囲気、静かな展開、安心できる結末、美しい自然描写、瞑想的な内容などによってもたらされる、心の平穏、リラックスした状態、安らぎ。「落ち着く」「癒やされる」「穏やかな気持ち」「心が静まる」というポジティブな低覚醒状態。
*   **判断基準 (ラベル=1):** テキストが、作品の内容や雰囲気によって、明確に**心の平穏、リラックス、安らぎ、落ち着き**を感じていることを表現している場合。
*   **具体例 (ラベル=1):**
    *   「読んでいるうちに、心が洗われるように穏やかな気持ちになれた。」
    *   「静かで優しい世界観に触れて、日々のストレスから解放され、癒やされた。」
    *   「激しい出来事の後、最後は静かに落ち着いて終わったので、安らかな気持ちで本を閉じられた。」
*   **具体例 (ラベル=0):**
    *   「危機が去ってほっとした。」（→Relief）
    *   「結末にとても満足した。」（→Satisfaction）
    *   「退屈で何も感じなかった。」（→Boredom）
*   **類似カテゴリーとの区別:**
    *   *Relief:* 緊張からの解放ではなく、持続的な「平穏」な心地よさ。
    *   *Joy:* より高揚した喜びではなく、静かで落ち着いたポジティブ感情。
    *   *Satisfaction:* 目標達成や期待充足の感覚ではなく、心の平穏さ。
    *   *Aesthetic Appreciation:* 美しさへの感動だけでなく、心の落ち着きや安らぎが中心。

**(11) Confusion (困惑)**
*   **定義:** 物語の筋、登場人物の動機、時間軸の錯綜、専門用語、難解な表現、曖昧な結末などが理解できず、当惑したり、わけがわからないと感じている状態。「よくわからない」「どういうこと？」「ついていけない」「混乱した」という認知的な困難さや理解不能感。
*   **判断基準 (ラベル=1):** テキストが、作品の内容や構造に対して、明確に**理解できないこと、わけがわからないこと、当惑**を表現している場合。
*   **具体例 (ラベル=1):**
    *   「時間軸が頻繁に飛ぶので、今どの時点の話なのか混乱してしまった。」
    *   「結局、あの登場人物がなぜあんな行動を取ったのか、最後まで理解できなかった。困惑している。」
    *   「哲学的な議論が難解すぎて、正直ついていけなかった。」
*   **具体例 (ラベル=0):**
    *   「結末の謎についてもっと知りたい。」（→Interest, Craving）
    *   「登場人物の行動に驚いた。」（→Surprise）
    *   「社会的な状況が気まずかった。」（→Awkwardness）
*   **類似カテゴリーとの区別:**
    *   *Interest:* 知りたいという好奇心ではなく、理解できないことによる「当惑」。
    *   *Awe:* 理解を超えたものへの圧倒感ではなく、理解しようとしてできない混乱。
    *   *Surprise:* 予期せぬ出来事への反応ではなく、理解不能な状況への反応。
    *   *Awkwardness:* 社会的な気まずさではなく、内容理解の困難さ。

**(12) Craving (渇望)**
*   **定義:** 物語の続き、謎の解明、特定のキャラクターの再登場、あるいは作中の食べ物、場所、体験などに対する、非常に強い欲求や待ちきれない気持ち。「続きが読みたい！」「早く知りたい！」「〇〇（キャラ）にまた会いたい！」「あの料理が食べたい！」という強い欲求。
*   **判断基準 (ラベル=1):** テキストが、物語の続き、情報、キャラクター、作中の対象物などに対して、明確に**強い欲求、待ちきれない気持ち、渇望感**を表現している場合。「〜したくてたまらない」「〜が欲しい」といった強い表現が手がかり。
*   **具体例 (ラベル=1):**
    *   「こんなクリフハンガーで終わるなんて！早く続編を読ませてくれ！渇望している！」
    *   「あの謎の真相が気になりすぎて、他のことが手につかない。」
    *   「作中に出てきた異世界の料理が、あまりに美味しそうで本気で食べたくなった。」
*   **具体例 (ラベル=0):**
    *   「今後の展開が楽しみだ。」（→Excitement, Interest）
    *   「結末がどうなるか気になる。」（→Interest, Anxiety）
    *   「素敵な場所だと思った。」（→Aesthetic Appreciation, Joy）
*   **類似カテゴリーとの区別:**
    *   *Interest:* 一般的な関心や好奇心よりも、はるかに「強い」欲求。
    *   *Excitement:* 期待感だけでなく、特定の対象への「渇望」に近い欲求。
    *   *Envy:* 他者が持つものへの羨望ではなく、自分が何かを得たい、体験したいという欲求。

**(13) Disgust (嫌悪)**
*   **定義:** 作中の不快な描写（グロテスク、不衛生、生理的に受け付けないもの）、登場人物の卑劣な行為、受け入れがたい思想などに対する、強い不快感、反感、拒絶感。「気持ち悪い」「生理的に無理」「反吐が出る」「汚らわしい」といった感覚。
*   **判断基準 (ラベル=1):** テキストが、作品内の特定の要素（描写、行動、思想など）に対して、明確に**強い不快感、反感、生理的な拒絶感**を表現している場合。
*   **具体例 (ラベル=1):**
    *   「戦闘シーンの生々しい描写がグロテスクすぎて、気分が悪くなった。嫌悪感でいっぱいだ。」
    *   「登場人物の自己中心的で卑劣な考え方には、生理的な嫌悪感を覚える。」
    *   「社会の腐敗を描いた部分が、あまりに汚らわしくて反吐が出そうだった。」
*   **具体例 (ラベル=0):**
    *   「彼の行動には怒りを感じた。」（→Anger）
    *   「ホラー描写が怖かった。」（→Fear, Horror）
    *   「単調でつまらなかった。」（→Boredom）
*   **類似カテゴリーとの区別:**
    *   *Anger:* 憤りや攻撃性よりも、「不快感」「拒絶感」が中心。
    *   *Horror:* 恐怖と結びついた嫌悪ではなく、嫌悪感そのものが中心。
    *   *Sadness:* 悲しみではなく、不快感や反感。

**(14) Empathic Pain (共感による痛み)**
*   **定義:** 登場人物が経験する苦痛（物理的、精神的）、悲劇、困難、喪失などに対して、読者自身がまるで自分のことのように感じ、心を痛めたり、深く同情したりする感情。「つらい」「かわいそう」「胸が痛む」「苦しい」「感情移入して泣いた」という感情移入による苦痛。
*   **判断基準 (ラベル=1):** テキストが、作中の**他者（登場人物など）の苦痛や困難**に対して、読者自身が明確に**心を痛めている、苦しみを感じている、深く同情している**ことを表現している場合。「〜の気持ちを考えるとつらい」「〜がかわいそうで見ていられない」などの表現が手がかり。
*   **具体例 (ラベル=1):**
    *   「主人公が長年耐えてきた孤独と苦しみを思うと、胸が締め付けられて涙が止まらなかった。」
    *   「子供が虐待される場面は、読んでいて本当に辛く、自分の心まで傷つくようだった。」
    *   「彼の絶望が痛いほど伝わってきて、ただただ苦しかった。」
*   **具体例 (ラベル=0):**
    *   「悲しい結末だった。」（→Sadness）
    *   「彼の勇気には感服した。」（→Admiration）
    *   「気まずい状況に同情した。」（→Awkwardness, Sympathy (本リスト外)）
*   **類似カテゴリーとの区別:**
    *   *Sadness:* 一般的な悲しみよりも、特定の他者の「苦痛への共感」が明確な場合。
    *   *Admiration:* 苦境に耐える姿への賞賛ではなく、苦痛の共有。
    *   *Awkwardness:* 社会的な気まずさへの共感ではなく、苦痛や困難への共感。
    *   *(注意)* Cowen & Keltnerの研究ではSympathyは別カテゴリーとして扱われたが、最終的な27リストからは除外された [4, 14]。本カテゴリーは、より強い「痛み」の共有に焦点を当てる。

**(15) Entrancement (夢中)**
*   **定義:** 物語の世界に完全に引き込まれ、時間や周りのことを忘れて没頭している状態。強い集中、我を忘れるほどの魅力、恍惚感。「没頭した」「我を忘れて読みふけった」「世界に浸れた」「引き込まれた」という状態。
*   **判断基準 (ラベル=1):** テキストが、読書体験中に**完全に没頭し、集中し、時間や現実を忘れるほど引き込まれた**状態を明確に表現している場合。
*   **具体例 (ラベル=1):**
    *   「面白すぎて、気づいたら夜が明けていた。完全に我を忘れて読みふけっていた。」
    *   「物語の世界観にどっぷり浸って、読み終えた後もしばらく現実に戻れなかった。」
    *   「一気読みしてしまった。それほどまでに引き込まれる魅力があった。」
*   **具体例 (ラベル=0):**
    *   「とても興味深い内容だった。」（→Interest）
    *   「ワクワクする展開だった。」（→Excitement）
    *   「美しい文章に感動した。」（→Aesthetic Appreciation）
*   **類似カテゴリーとの区別:**
    *   *Interest:* 一般的な関心よりも、はるかに深い「没入感」。
    *   *Excitement:* 興奮状態だけでなく、集中し没頭する状態。
    *   *Joy/Aesthetic Appreciation:* これらの感情を伴うことが多いが、Entrancementは「没入」という状態そのものに焦点を当てる。

**(16) Excitement (興奮)**
*   **定義:** スリリングな展開、アクションシーン、どんでん返し、今後の展開への期待感、嬉しいニュースなどによって引き起こされる、高揚感、期待、ドキドキする感覚、活気づく気持ち。「ワクワクする」「ドキドキした」「テンションが上がった」「待ちきれない！」というポジティブな高覚醒状態。
*   **判断基準 (ラベル=1):** テキストが、作品の展開や内容に対して、明確に**高揚感、期待感、スリル、活気づく感覚**を表現している場合。「ワクワク」「ドキドキ」「楽しみ」などの表現が手がかり。
*   **具体例 (ラベル=1):**
    *   「クライマックスの戦闘シーンは手に汗握る展開で、読んでいて最高に興奮した！」
    *   「まさかのどんでん返しに鳥肌！テンションが上がった！」
    *   「次巻の発売が待ちきれない！どんな展開になるかワクワクが止まらない！」
*   **具体例 (ラベル=0):**
    *   「今後の展開が心配だ。」（→Anxiety）
    *   「とても面白い話だった。」（→Joy, Interest, Amusementなど文脈による）
    *   「物語に完全に没頭した。」（→Entrancement）
*   **類似カテゴリーとの区別:**
    *   *Anxiety:* ネガティブな心配ではなく、ポジティブな「期待感」「スリル」。
    *   *Joy:* より穏やかな喜びではなく、高揚感を伴う。
    *   *Interest:* 知的な関心だけでなく、感情的な高揚や期待感。
    *   *Craving:* 強い欲求だけでなく、期待やスリルによる高揚感。

**(17) Fear (恐怖)**
*   **定義:** 作中の脅威（敵、怪物、危険な状況、追跡、超常現象、心理的脅威など）によって引き起こされる、身の危険や不快な事態を感じるような直接的な恐れ。「怖い」「恐ろしい」「ぞっとした」「逃げたい」「生きた心地がしない」という感情。
*   **判断基準 (ラベル=1):** テキストが、作品内の**具体的または心理的な脅威**に対して、明確に**恐れ、怖さ、危険を感じる感覚**を表現している場合。
*   **具体例 (ラベル=1):**
    *   「暗闇から何かが現れる場面は、本気で怖くてページをめくるのがためらわれた。」
    *   「正体不明の存在に追われるシーンは、息が詰まるほど恐ろしかった。」
    *   「登場人物が精神的に追い詰められていく描写に、ぞっとするような恐怖を感じた。」
*   **具体例 (ラベル=0):**
    *   「これからどうなるか不安だ。」（→Anxiety）
    *   「グロテスクな描写に嫌悪感を覚えた。」（→Disgust）
    *   「衝撃的な展開に戦慄した。」（→Horror）
*   **類似カテゴリーとの区別:**
    *   *Anxiety:* 未来への漠然とした不安ではなく、現在進行形または具体的な「脅威」への反応。
    *   *Horror:* 嫌悪感や衝撃を伴う強い恐怖ではなく、恐怖そのものが中心。
    *   *Awe:* 偉大さへの畏れではなく、危険や脅威への恐れ。
    *   *Surprise:* 単なる驚きではなく、脅威を伴う驚き（重なる場合もある）。

**(18) Horror (戦慄)**
*   **定義:** 極度の恐怖に加えて、ショック、嫌悪感、不気味さ、残虐さ、おぞましさなどが入り混じった、非常に強い不快な感情。「ゾッとした」「血の気が引いた」「おぞましい」「身の毛がよだつ」「吐き気がするほど怖い」といった感覚。しばしば衝撃的な出来事や描写に関連する。
*   **判断基準 (ラベル=1):** テキストが、作品内の出来事や描写に対して、**極度の恐怖**に加えて、**強い嫌悪感、ショック、不気味さ、残虐さへの反応**を明確に示している場合。FearやDisgust単独では表現しきれない、複合的で強烈なネガティブ感情。
*   **具体例 (ラベル=1):**
    *   「あの残虐極まりないシーンには、恐怖と嫌悪感で体が震え、戦慄した。」
    *   「想像を絶するおぞましい描写に、血の気が引くような感覚を覚えた。」
    *   「不気味な真相が明らかになった瞬間、恐怖で叫び出しそうになり、吐き気すら感じた。」
*   **具体例 (ラベル=0):**
    *   「ただただ怖かった。」（→Fear）
    *   「気持ち悪い描写だった。」（→Disgust）
    *   「衝撃的な結末に驚いた。」（→Surprise）
*   **類似カテゴリーとの区別:**
    *   *Fear:* 純粋な恐怖に、強い「嫌悪感」「衝撃」「おぞましさ」などが加わったもの。
    *   *Disgust:* 嫌悪感に、強い「恐怖」「衝撃」が加わったもの。
    *   *Surprise:* 単なる驚きではなく、恐怖や嫌悪を伴う衝撃的な驚き。
    *   *(注意)* 感情の勾配（Anxiety→Fear→Horror→Disgust）[6, 1, 3, 5] を考慮し、境界事例は慎重に判断。

**(19) Interest (興味)**
*   **定義:** 物語の謎、新しい情報、未知の世界観、特定のキャラクターの背景や心理、テーマ、専門的な内容などに対して抱く、知りたい、もっと読みたい、関わりたいという好奇心や知的な関心。「面白い（知的に）」「気になる」「もっと知りたい」「興味深い」「関心がある」という認知的・感情的なエンゲージメント。
*   **判断基準 (ラベル=1):** テキストが、作品の内容や要素に対して、明確に**知的な好奇心、関心、もっと知りたいという欲求**を表現している場合。「なぜ？」「どうなっているの？」といった問いかけを含むこともある。
*   **具体例 (ラベル=1):**
    *   「この独特な世界観の設定が非常に興味深く、もっと詳しく知りたくなった。」
    *   「事件の真相に繋がる伏線が散りばめられていて、犯人が誰なのか気になって仕方がない。」
    *   「登場人物の複雑な心理描写に興味を惹かれ、彼の過去についてもっと読みたくなった。」
*   **具体例 (ラベル=0):**
    *   「展開が面白くて笑った。」（→Amusement）
    *   「続きが楽しみでワクワクする。」（→Excitement）
    *   「内容が難しくて混乱した。」（→Confusion）
*   **類似カテゴリーとの区別:**
    *   *Amusement:* 笑いやユーモアではなく、知的な関心。
    *   *Excitement:* 感情的な高揚感よりも、知的な好奇心。
    *   *Confusion:* 理解できない当惑ではなく、知りたいという関心。
    *   *Craving:* 強い渇望ではなく、知的な関心や探求心。
    *   *Entrancement:* 没頭状態そのものではなく、内容への関心。

**(20) Joy (喜び)**
*   **定義:** ハッピーエンド、登場人物の成功や幸福、心温まる交流、共感できるポジティブな出来事、読書体験そのものから得られる幸福感、楽しさ、満足感、嬉しい気持ち。「楽しい」「嬉しい」「幸せ」「良かった」「感動した（ポジティブな意味で）」という広範なポジティブ感情。
*   **判断基準 (ラベル=1):** テキストが、作品の内容や読書体験全体に対して、明確に**幸福感、楽しさ、嬉しさ、ポジティブな感動**といった、全般的なポジティブ感情を表現している場合。
*   **具体例 (ラベル=1):**
    *   「読み終わった後、心が温かくなって、とても幸せな気持ちになれた。」
    *   「主人公たちが困難を乗り越えて結ばれたシーンは、本当に嬉しくて感動した。」
    *   「この本に出会えて良かった！読んでいる間ずっと楽しかった。」
*   **具体例 (ラベル=0):**
    *   「ユーモラスな会話に笑った。」（→Amusement）
    *   「スリリングな展開に興奮した。」（→Excitement）
    *   「結末に満足した。」（→Satisfaction）
    *   「危機を脱してほっとした。」（→Relief）
    *   「美しい文章に感動した。」（→Aesthetic Appreciation）
*   **類似カテゴリーとの区別:**
    *   *Amusement, Excitement, Satisfaction, Relief, Aesthetic Appreciation, Calmness* など、より具体的なポジティブ感情が特定できる場合はそちらを優先するが、Joyはこれらの感情と**共存**することも多い。テキストが特定の側面だけでなく、**全般的な幸福感や楽しさ**を表現している場合にJoyを付与する。

**(21) Nostalgia (懐旧)**
*   **定義:** 作中の描写（時代設定、風景、出来事、音楽、風俗、アイテムなど）が、読者自身の過去の経験、思い出、あるいは失われた時代への憧憬と結びつき、甘酸っぱい、感傷的な、あるいは温かい気持ちを呼び起こすこと。「懐かしい」「あの頃を思い出す」「センチメンタルな気分」「郷愁を感じる」という感情。
*   **判断基準 (ラベル=1):** テキストが、作品の要素と**読者自身の過去の経験や記憶、あるいは特定の時代**とを結びつけ、明確に**懐かしさ、感傷、郷愁**の念を表現している場合。
*   **具体例 (ラベル=1):**
    *   「描かれている昭和の街並みが、自分の子供時代と重なって、とても懐かしい気持ちになった。」
    *   「作中で流れる昔のヒット曲に、青春時代を思い出して甘酸っぱい感傷に浸った。」
    *   「もう失われてしまった古き良き時代の雰囲気に、強い郷愁を感じた。」
*   **具体例 (ラベル=0):**
    *   「昔を舞台にした歴史小説として興味深かった。」（→Interest）
    *   「登場人物の過去の悲劇に悲しくなった。」（→Sadness, Empathic Pain）
    *   「美しい故郷の描写に感動した。」（→Aesthetic Appreciation, Joy）
*   **類似カテゴリーとの区別:**
    *   *Sadness:* 悲しみだけでなく、過去への「感傷」や「甘酸っぱさ」を伴う。
    *   *Joy:* 喜びだけでなく、過去を振り返る「懐かしさ」が中心。
    *   *Interest:* 知的な関心ではなく、過去への感情的な結びつき。

**(22) Relief (安堵)**
*   **定義:** 続いていた緊張状態（危機、不安、心配、困難）が解消され、危険が去ったり、問題が解決したり、悪い結果が回避されたりしたことによって感じる、ほっとした気持ち、肩の荷が下りるような感覚、緊張からの解放感。「ほっとした」「良かった（安堵の意味で）」「安心した」「助かった」「緊張が解けた」というネガティブからポジティブへの移行。
*   **判断基準 (ラベル=1):** テキストが、**特定の緊張状態や心配事が解消された**ことに対して、明確に**安堵感、安心感、緊張からの解放**を表現している場合。「〜でほっとした」「〜で安心した」などの表現が手がかり。
*   **具体例 (ラベル=1):**
    *   「主人公が絶体絶命の危機を脱したと分かって、心底ほっとした。」
    *   「ずっと心配していた問題が無事に解決して、ようやく肩の荷が下りた。安心した。」
    *   「最悪の事態は避けられたようで、良かったと安堵のため息をついた。」
*   **具体例 (ラベル=0):**
    *   「全体的に穏やかな気持ちになれた。」（→Calmness）
    *   「ハッピーエンドで嬉しかった。」（→Joy）
    *   「結末に満足した。」（→Satisfaction）
*   **類似カテゴリーとの区別:**
    *   *Joy:* 一般的な喜びではなく、特定の「緊張からの解放」によって生じる。
    *   *Calmness:* 持続的な平穏さではなく、緊張緩和による瞬間的な安堵感。
    *   *Satisfaction:* 目標達成や期待充足ではなく、心配事の解消。

**(23) Romance (ロマンス)**
*   **定義:** 登場人物間の恋愛感情、愛情表現（言葉、行動）、親密な関係性、デートシーン、恋愛の始まりや成就などに対して、読者が感じる甘美さ、ときめき、温かい気持ち、あるいは恋愛への憧れ。「キュンとした」「ときめいた」「甘酸っぱい」「二人の関係が素敵」「うらやましい（恋愛に関して）」という感情。
*   **判断基準 (ラベル=1):** テキストが、作中の**恋愛的な要素（感情、関係、出来事）**に対して、明確に**ときめき、甘美さ、温かい気持ち、憧れ**などを表現している場合。
*   **具体例 (ラベル=1):**
    *   「不器用だけど真っ直ぐな彼の告白シーンに、思わずキュンとしてしまった。」
    *   「二人の甘いやり取りを読んでいると、こっちまで幸せな気持ちになってときめく。」
    *   「こんな風にお互いを想い合える関係って素敵だな、と憧れた。」
*   **具体例 (ラベル=0):**
    *   「登場人物への強い愛着を感じる。」（→Adoration）
    *   「性的な描写に興奮した。」（→Sexual Desire）
    *   「二人が結ばれて嬉しかった。」（→Joy, Satisfaction）
*   **類似カテゴリーとの区別:**
    *   *Adoration:* 熱愛や崇拝ではなく、主に「恋愛」に関連するポジティブな感情やときめき。
    *   *Joy:* 一般的な喜びよりも、恋愛要素に特化した感情。
    *   *Sexual Desire:* 性的な欲求ではなく、感情的な繋がりやときめき。
    *   *Envy:* 他の側面（才能、富など）への羨望ではなく、恋愛関係への羨望。

**(24) Sadness (悲しみ)**
*   **定義:** 作中の喪失（死、別れ、機会損失）、失敗、不幸な出来事、報われない思い、やるせない雰囲気、悲劇的な結末などによって引き起こされる、悲しい、切ない、憂鬱な、心が痛む、涙が出る、落ち込むといった感情。「悲しい」「切ない」「泣けた」「つらい」「胸が痛む」「やるせない」という広範なネガティブ感情。
*   **判断基準 (ラベル=1):** テキストが、作品の内容や結末に対して、明確に**悲しみ、切なさ、憂鬱、心の痛み**といった、全般的なネガティブ感情を表現している場合。
*   **具体例 (ラベル=1):**
    *   「愛する人との永遠の別れの場面は、あまりにも悲しくて涙が止まらなかった。」
    *   「努力が報われず、夢破れた主人公の姿に、深い悲しみを感じた。」
    *   「読後、やるせない気持ちと重い悲しみに包まれて、しばらく立ち直れなかった。」
*   **具体例 (ラベル=0):**
    *   「登場人物の苦しみに共感して辛かった。」（→Empathetic Pain）
    *   「理不尽な展開に怒りを感じた。」（→Anger）
    *   「不快な描写に嫌悪感を覚えた。」（→Disgust）
    *   「退屈でつまらなかった。」（→Boredom）
*   **類似カテゴリーとの区別:**
    *   *Empathetic Pain:* 他者の苦痛への共感が中心ではなく、より広範な悲しみ。ただし共存することも多い。
    *   *Anger:* 怒りではなく、悲しみや喪失感。
    *   *Disgust:* 嫌悪感ではなく、悲しみ。
    *   *Boredom:* 退屈さではなく、悲しみ。
    *   *Nostalgia:* 過去への感傷ではなく、現在の悲しみ。

**(25) Satisfaction (満足)**
*   **定義:** 物語の結末、伏線の回収、謎の解明、キャラクターの成長、問題の解決、期待通りの展開、読了感などに対して感じる、満たされた気持ち、納得感、達成感、すっきりした感覚。「満足した」「すっきりした」「納得した」「読んでよかった（満足の意味で）」「期待通りだった」という感覚。
*   **判断基準 (ラベル=1):** テキストが、物語の結末、構成、内容、読書体験全体に対して、明確に**満たされた感覚、納得感、達成感、期待が満たされた感覚**を表現している場合。
*   **具体例 (ラベル=1):**
    *   「散りばめられた伏線が最終章で見事に回収され、非常に満足のいく読後感だった。」
    *   「主人公が困難を乗り越え成長していく姿を見届けられて、心から満足した。」
    *   「長編だったけど、最後まで読み通して大きな達成感と満足感がある。」
    *   「期待通りのハッピーエンドで、すっきり満足して本を閉じられた。」
*   **具体例 (ラベル=0):**
    *   「とても嬉しくて幸せな気持ちになった。」（→Joy）
    *   「緊張が解けてほっとした。」（→Relief）
    *   「穏やかな気持ちになれた。」（→Calmness）
    *   「結末には不満が残った。」（→Anger, Sadnessなど）
*   **類似カテゴリーとの区別:**
    *   *Joy:* 一般的な喜びよりも、期待が満たされたり、目標が達成されたりしたことによる「充足感」「納得感」。
    *   *Relief:* 心配事の解消による安堵ではなく、期待充足や達成感。
    *   *Calmness:* 平穏さではなく、満たされた感覚。
    *   *Admiration:* 質への賞賛だけでなく、読者自身の満足感。

**(26) Sexual Desire (性的欲求)**
*   **定義:** 作中のエロティックな描写、登場人物の肉体的な魅力、官能的な雰囲気、特定の状況などに対して、読者が感じる性的な興奮や欲求。「興奮した（性的な意味で）」「ドキドキした（性的な意味で）」「色気を感じる」「官能的だ」といった感覚。
*   **判断基準 (ラベル=1):** テキストが、作品の**性的な要素（描写、キャラクター、雰囲気など）**に対して、明確に**性的な興奮、欲求、魅力を感じている**ことを表現している場合。
*   **具体例 (ラベル=1):**
    *   「二人の情熱的なシーンの描写は非常に官能的で、読んでいてドキドキした。」
    *   「登場人物の肉体美に関する描写に、思わず性的な興奮を覚えてしまった。」
    *   「言葉遣いや仕草に妙な色気があって、煽情的に感じた。」
*   **具体例 (ラベル=0):**
    *   「二人の恋愛模様にときめいた。」（→Romance）
    *   「登場人物の美しさに感動した。」（→Aesthetic Appreciation）
    *   「彼のカリスマ性に惹かれた。」（→Admiration, Adoration）
*   **類似カテゴリーとの区別:**
    *   *Romance:* 恋愛感情やときめきではなく、明確に「性的」な要素への反応。
    *   *Adoration:* 熱愛や崇拝ではなく、性的な魅力や興奮。
    *   *Aesthetic Appreciation:* 美しさへの感動ではなく、性的な魅力。
    *   *Excitement:* 一般的な興奮ではなく、性的な興奮。

**(27) Surprise (驚き)**
*   **定義:** 予期せぬ出来事、予想外の展開（どんでん返し）、意外な情報、キャラクターの予期せぬ行動などに対する、瞬間的な反応。「えっ！？」「びっくりした」「まさか！」「予想外だった」「驚いた」という感情。ポジティブ、ネガティブ、ニュートラルのいずれの場合もある。
*   **判断基準 (ラベル=1):** テキストが、作品内の**予期せぬ出来事や情報**に対して、明確に**驚き、意外性**を感じていることを表現している場合。
*   **具体例 (ラベル=1):**
    *   「まさかあの人物が犯人だったとは！最後のどんでん返しには本当に驚いた。」
    *   「突然の告白に、びっくりして言葉を失った。」
    *   「物語が予想もしない方向に進んでいき、ただただ驚きの連続だった。」
*   **具体例 (ラベル=0):**
    *   「壮大なスケールに圧倒された。」（→Awe）
    *   「衝撃的な展開に戦慄した。」（→Horror）
    *   「今後の展開が気になる。」（→Interest）
    *   「理解できず混乱した。」（→Confusion）
*   **類似カテゴリーとの区別:**
    *   *Awe:* スケールや深遠さへの圧倒感ではなく、予期せぬことへの反応。
    *   *Horror:* 恐怖や嫌悪を伴う衝撃ではなく、純粋な（あるいは他の感情を伴う）驚き。
    *   *Excitement:* ポジティブな期待感ではなく、予期せぬ出来事への反応。
    *   *Confusion:* 理解不能感ではなく、予期せぬことへの反応。
    *   *Fear:* 脅威への反応ではなく、予期せぬことへの反応（脅威を伴う驚きの場合はFearも共存しうる）。

---

## 6. アノテーション手順

1.  **テキスト読解:** 割り当てられたテキストを注意深く、最後まで読んでください。内容、文脈、ニュアンスを把握します。
2.  **読者の感情特定:** テキスト全体を通して、書き手（読者）が**自身の感情**として表現している箇所を特定します。
3.  **カテゴリー照合:** 特定された感情表現が、セクション5で定義された27の感情カテゴリーのいずれかに該当するかを検討します。
4.  **「有無」判断:** 各カテゴリーについて、テキスト中にその感情が存在する**明確な根拠**があるかを判断します。
    *   明確な根拠がある → ラベル = 1 (存在する)
    *   明確な根拠がない、曖昧、確信が持てない → ラベル = 0 (存在しない)
5.  **マルチラベル選択:** 該当する（ラベル=1と判断した）感情カテゴリーを**すべて**選択します。該当するものが一つもない場合は、何も選択しません。
6.  **結果記録:** 選択したラベル（またはラベルなし）を、指定された出力フォーマット（セクション9参照）に従って記録します。
7.  **次のテキストへ:** 次のテキストに進み、ステップ1から繰り返します。

## 7. 特定ケースへの対応

### 7.1. マルチラベリング（複数の感情が同時に存在する場合）
一つのテキストが複数の感情を表現していることは一般的です（例: 喜びと安堵、悲しみと怒りなど）[11]。それぞれの感情について「有無」を独立して判断し、**存在する（ラベル=1）と判断できるものはすべて選択**してください。

### 7.2. 曖昧さ・不確実性への対応
*   **判断基準:** ある感情が存在するかどうか判断に迷う場合、複数の解釈が可能で確信が持てない場合、または表現が非常に曖昧な場合は、**「存在しない（ラベル=0）」**と判断してください。無理に分類せず、「明確な根拠」があるものだけを選択する原則を徹底します。
*   **感情の勾配:** 感情間には明確な境界がない場合があること [6, 1, 2, 3, 5] を念頭に置いてください。境界事例（例: FearとHorrorの間）では、より強く特徴が現れているカテゴリー、または両方のカテゴリーに明確な根拠がある場合にのみラベルを付与します。
*   **感情なし:** テキストが感情を全く表現していない（例: 事実のみの記述、客観的な分析）、またはどのカテゴリーにも明確に該当しない場合は、どのラベルも選択せず、結果として空のリストを出力します（セクション9参照）。

### 7.3. 読者の感情 vs 登場人物の感情
*   **区別の原則:** アノテーションの対象は、**テキストの書き手（読者）が表明している自身の感情**のみです。作中の登場人物が感じている感情の描写や、書き手が登場人物の感情について推測している記述は、**対象外**です。
*   **具体例:**
    *   **対象外:** 「主人公は深い悲しみに打ちひしがれていた。」（登場人物の感情描写）
    *   **対象外:** 「おそらく彼は、裏切られた怒りを感じていたのだろう。」（書き手による登場人物の感情推測）
    *   **対象（Sadness, Empathic Pain）:** 「主人公が悲しんでいるのを見て、私も胸が締め付けられ、悲しくなった。」（読者自身の感情表明）
    *   **対象（Anger）:** 「彼の身勝手な行動には、読んでいるこちらが腹が立った。」（読者自身の感情表明）

### 7.4. 皮肉・反語などの解釈
*   **原則:** 皮肉や反語（例: 「最高に面白かったよ（棒読み）」）が使われている場合、表面的な言葉ではなく、文脈から読み取れる**書き手の真の感情**に基づいて「有無」を判断してください。
*   **判断困難な場合:** 皮肉の意図が非常に曖昧で、真の感情を特定することに著しい困難が伴う場合は、無理に判断せず、その感情は「存在しない（ラベル=0）」と判断するか、可能であれば**特定のフラグを立ててレビューを依頼**してください（フラグ付けの仕組みは別途指示します）。

## 8. アノテーション具体例

以下に、いくつかのテキスト例と、それに対して付与されるべきラベル（存在する感情カテゴリーのリスト）、および簡単な根拠を示します。

**例1:**
*   **テキスト:** 「読み終えたばかりだけど、主人公が長年の苦闘の末にようやく安らぎを見出す最後の場面には涙が止まらなかった。それは純粋な幸福というより、道中で失われた全てに対する消えない悲しみと入り混じった、深い安堵感だった。文章もただただ素晴らしかった。」
*   **付与ラベル:** ``
*   **根拠:** 「深い安堵感」→ Relief。「消えない悲しみ」→ Sadness。「文章もただただ素晴らしかった」→ Aesthetic Appreciation。「涙が止まらなかった」はRelief/Sadnessの強度を支持。「純粋な幸福というより」はJoyを除外する根拠。

**例2:**
*   **テキスト:** 「この展開はちょっと無理がある気がするなぁ。なんで急にそうなったのか、説明不足でよく分からなかった。」
*   **付与ラベル:** `["Confusion"]`
*   **根拠:** 「説明不足でよく分からなかった」がConfusionの明確な根拠。

**例3:**
*   **テキスト:** 「主人公の気持ちを考えると、ただただ悲しい。彼がどれだけ辛かったか、痛いほど伝わってきた。」
*   **付与ラベル:** ``
*   **根拠:** 「ただただ悲しい」→ Sadness。「気持ちを考えると」「痛いほど伝わってきた」→ Empathic Pain。

**例4:**
*   **テキスト:** 「最高！めっちゃ面白い！特に登場人物たちの掛け合いが絶妙で、何度も声出して笑った。読後感もすごく満足。」
*   **付与ラベル:** ``
*   **根拠:** 「最高！めっちゃ面白い！」→ Joy。「掛け合いが絶妙で、何度も声出して笑った」→ Amusement。「読後感もすごく満足」→ Satisfaction。

**例5:**
*   **テキスト:** 「うーん、期待してたほどではなかったかな。全体的に話が単調で、途中で飽きてしまった。」
*   **付与ラベル:** ``
*   **根拠:** 「全体的に話が単調で、途中で飽きてしまった」がBoredomの明確な根拠。「期待してたほどではなかった」はSadnessやAngerの可能性もあるが、続く理由付けがBoredomを強く示唆するため、Boredomのみを選択。

**例6:**
*   **テキスト:** 「この小説は、1980年代の日本の地方都市が舞台になっている。主人公は高校生で、友人関係や進路に悩んでいる。」
*   **付与ラベル:** `` (空リスト)
*   **根拠:** テキストはあらすじや設定の客観的な記述であり、読者自身の感情表現が含まれていない。

**例7:**
*   **テキスト:** 「ラストのどんでん返しには本当にびっくりした！まさかあの人が黒幕だったなんて…。でも、全ての伏線が見事に繋がって、読後はすごくスッキリして満足感がすごい。」
*   **付与ラベル:** ``
*   **根拠:** 「本当にびっくりした！まさか…」→ Surprise。「伏線が見事に繋がって」「スッキリして満足感がすごい」→ Satisfaction。

## 9. 出力フォーマットの定義

アノテーション結果は、**JSON Lines** 形式で記録・提出してください。
各行が一つのテキストに対応するJSONオブジェクトとなります。

**形式:**
各行のJSONオブジェクトは以下のキーを持ちます。

*   `"text_id"`: テキストを一意に識別するID（文字列または数値）。
*   `"text"`: アノテーション対象の原文テキスト（文字列）。
*   `"labels"`: そのテキストに存在すると判断された感情カテゴリーの**英語名**（セクション4のリスト参照）を要素とする**リスト（配列）**。リスト内の順序は問いません。該当する感情がない場合は、**空のリスト ``** とします。

**例:**

```json
{"text_id": "review_001", "text": "最高！めっちゃ面白い！特に登場人物たちの掛け合いが絶妙で、何度も声出して笑った。読後感もすごく満足。", "labels":}
{"text_id": "comment_045", "text": "この展開はちょっと無理がある気がするなぁ。なんで急にそうなったのか、説明不足でよく分からなかった。", "labels": ["Confusion"]}
{"text_id": "blogpost_123", "text": "この小説は、1980年代の日本の地方都市が舞台になっている。主人公は高校生で、友人関係や進路に悩んでいる。", "labels":}
```

## 10. アノテーションすべきでないこと（注意点）

*   **個人的な感情の投影:** あなた自身がそのテキストを読んでどう感じたかではなく、テキストの書き手が表現している感情を捉えてください。
*   **過剰な推測:** テキストに明確な根拠がないのに、「きっとこう感じているはずだ」と推測してラベルを付けないでください。
*   **登場人物の感情へのラベリング:** 作中の登場人物の感情描写そのものにラベルを付けないでください（セクション7.3参照）。
*   **リスト外の感情の使用:** 定義された27カテゴリー以外の感情（例: 「イライラ」「がっかり」「誇り」など）で判断しないでください。最も近い定義を持つカテゴリーに該当するか、該当しないかを判断します。
*   **感情価（ポジティブ/ネガティブ）のみでの判断:** 単にポジティブかネガティブかだけでなく、どの具体的な感情カテゴリーに該当するかを判断してください。

## 11. 品質管理とアノテーター訓練

### 11.1. 品質管理
*   **一貫性の維持:** 高品質なデータセット構築のため、アノテーター間およびアノテーター内での判断の一貫性が重要です。本ガイドラインを常に参照し、一貫した基準で作業を行ってください。
*   **アノテーター間一致度 (IAA):** プロジェクトでは、アノテーションの一貫性を測るために、IAA指標（例: マルチラベルタスク用のKrippendorff's alpha、F1スコアなど）を定期的に計算し、フィードバックを行います。目標とする一致度レベルについては別途通知します。
*   **レビューとフィードバック:** アノテーション結果の一部はレビューされ、必要に応じてフィードバックが提供されます。フィードバックを参考に、判断基準の調整をお願いします。

### 11.2. アノテーター訓練
*   **初期トレーニング:** アノテーション開始前に、本ガイドラインに基づいたトレーニングセッションを実施します。ガイドラインの理解、カテゴリー定義の把握、具体例を用いた演習などが含まれます。
*   **キャリブレーション:** トレーニングの一環として、またはアノテーション期間中に、複数のアノテーターが同じテキストセットに対してアノテーションを行い、結果を比較・議論するキャリブレーション（調整）セッションを設けることがあります。これにより、判断基準のずれを修正し、解釈を統一します。
*   **継続的な学習:** アノテーション作業中に生じた疑問点や判断に迷うケースは、積極的に質問してください（セクション12参照）。これらの質疑応答やレビューを通じて得られた知見は、必要に応じてガイドラインの改訂（マイナーアップデート）に反映されることがあります。ガイドラインは「生きた文書」として、継続的に改善されます。専用のトレーニング資料が提供される場合もあります。

## 12. 連絡先・質問

アノテーション作業中に判断に迷うケースに遭遇した場合、本ガイドラインの記述が不明瞭な場合、またはその他質問がある場合は、以下の連絡先/方法で質問してください。

*   **連絡担当者:** [担当者名またはチーム名]
*   **連絡方法:** [メールアドレス、チャットツール名、課題管理システムなど]
*   **質問時の情報:** 質問する際には、**該当するテキストのID (`text_id`)** と、**具体的な質問内容（どの部分で、どのカテゴリーの判断に迷ったかなど）**を明確に記載してください。可能であれば、ご自身の判断とその根拠も添えていただけると、より的確な回答に繋がります。