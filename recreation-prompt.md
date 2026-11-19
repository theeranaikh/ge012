# Recreation prompt for Made in China / GE012

Recreate the supplied `index.html` as one standalone HTML file with inline CSS, HTML and vanilla JavaScript. Use its Thai wording, complete chapter paragraphs, SVG paths, and WOFF2 payloads. Use the four original Higgsfield sheets and the 22 crop rectangles below. Take the presentation content from `GE012-Final-Orientalism-diff.docx`. Use the complete 14-person group 127A roster on the Red Door foreword, including the supplied names, student IDs, roster numbers and responsibilities. Copy the roster markup and instructor name from the supplied HTML. The source describes a 4:20 video and a publication plan. Use `อ่านเนื้อหา` for the main call to action, which reveals the original report passages below the summary.

## Initial frame and content

Start on the VHS shelf, with Red Door (virtual index 11) turned out as book 01 of 11. It combines the original Red Door credits with the overview formerly under The Silent Valley. Opening Red Door shows the foreword, instructor, course, and all 14 members with IDs, roster numbers, and roles. The merged opening narrative follows the roster. Center the two-line cobalt logo `中国印象` over `MADE IN CHINA`. Put `เกี่ยวกับโครงงาน` on the left and `ศท.012 / ภาคเรียน 1 · 2569` on the right. The footer reads `สี่แยกปากแจ๋ว / GE012` on the left and `อ้างอิง / คณะผู้จัดทำ` on the right, with the latter two buttons opening the corresponding details.

Set the tab labels to `ทั้งหมด`, `ที่มา`, `วิเคราะห์`, `โครงงาน` and `สรุป` with jump indices 0, 1, 4, 6 and 9. The cobalt active block follows chapter groups 0–3, 4–5, 6–8 and 9–11. The following rows contain the art identifier, original English VHS title, Thai content heading, chapter metadata, summary, fallback color and report section name.

```js
const CHAPTERS = [
  ['door', 'Red Door', 'เปิดประตูสู่เรื่องเล่าของจีน', 'คำนำและเรื่องเปิดเล่ม', 'ถ้าพูดถึงจีน ภาพอะไรขึ้นมาก่อน กลุ่มสี่แยกปากแจ๋วเริ่มทำคลิปจากคำถามนี้ แล้วออกตามหาว่าใครเป็นคนเล่าเรื่องที่เราคุ้น', '#773a2e', 'คำนำ'],
  ['bluehour', 'The Blue Hour', 'เมื่อแสงเปลี่ยน ภาพจำเรื่องจีนก็เปลี่ยน', 'ที่มาและความสำคัญ', 'กำแพงเมืองจีน โคมแดง และสินค้าราคาถูกเป็นภาพที่เห็นซ้ำในสื่อ รายงานเริ่มจากคำถามว่าพอเห็นภาพเดิมบ่อย ๆ เรามองข้ามอะไรไปบ้าง', '#223350', 'ที่มาและความสำคัญของปัญหา'],
  ['river', 'River of Salt', 'สี่ทางที่จะมองจีนให้พ้นภาพจำ', 'เป้าหมายการสื่อสาร', 'โครงงานตั้งเป้าไว้สี่ข้อ ตั้งคำถามกับภาพจำ อธิบายประวัติศาสตร์และบูรพานิยม เปิดให้เห็นจีนร่วมสมัย และฝึกตรวจสอบข้อมูลก่อนเชื่อหรือแชร์', '#643d33', 'วัตถุประสงค์'],
  ['summer', 'The Last Summer', 'เมื่อเรื่องเล่าเปลี่ยนมือ มองจีนผ่านบูรพานิยม', 'Edward W. Said / 1978', 'เอ็ดเวิร์ด ซาอิดชวนให้ดูว่าใครมีอำนาจสร้างภาพของโลกตะวันออก ลองใช้คำถามนี้กับสื่อที่ดูอยู่ ใครเป็นคนเล่า เขาเลือกให้เราเห็นอะไร และอะไรอยู่นอกภาพ?', '#8d4537', 'ความรู้จาก Module'],
  ['green', 'The Green Road', 'เส้นทางจากเครื่องลายครามสู่สงครามฝิ่น', 'ประวัติศาสตร์ / ศตวรรษที่ 19', 'ยุโรปเคยนิยมผ้าไหมและเครื่องลายครามจากจีน ในศตวรรษที่ 19 การขยายอำนาจของชาติตะวันตกและสงครามค้าฝิ่นเกิดขึ้นพร้อมกับภาพจีนที่เปลี่ยนไปในงานเขียนตะวันตก', '#384635', 'การค้นคว้าและการวิเคราะห์'],
  ['noon', 'Noon in Ashes', 'จีนในแสงใหม่', 'เซินเจิ้นและ 56 กลุ่มชาติพันธุ์', 'เซินเจิ้นเป็นเขตเศรษฐกิจพิเศษตั้งแต่ปี 1980 และมี GDP 3.68 ล้านล้านหยวนในปี 2024 ส่วนสำมะโนปี 2020 สะท้อนความหลากหลายของจีนผ่านข้อมูลประชากร 56 กลุ่มชาติพันธุ์ที่รัฐรับรอง', '#554634', 'การค้นคว้าและการวิเคราะห์'],
  ['observer', 'The Observer', 'ดูสื่อให้เห็นว่าใครกำลังเล่า', 'ผู้ชมอายุ 15–25 ปี / TikTok', 'คลิปเปิดด้วยคำถามเรื่องภาพจำ แล้วพาย้อนประวัติศาสตร์ก่อนกลับมาดูจีนวันนี้ ท้ายคลิปชวนให้ผู้ชมลองตรวจดูว่าเรื่องที่เพิ่งได้ยินมาจากแหล่งไหน', '#33465a', 'แนวทางการแก้ไข'],
  ['birds', 'The Fallen Birds', 'เก็บภาพที่ตกหล่นมาเล่าใน Made in China', 'วิดีโอแนวตั้ง / 04:20 นาที', 'คลิปสลับเครื่องแต่งกายตามยุค ใช้ภาพประกอบและซับไตเติลช่วยเล่าเรื่องในห้าช่วง ตั้งแต่คำถามเปิดคลิปไปจนถึงคำถามที่ชวนผู้ชมกลับไปคิดต่อ', '#716335', 'ผลงานสร้างสรรค์'],
  ['storm', 'Light in the Storm', 'วัดผลอย่างไรในกระแสไวรัล', 'ผลที่คาดหวัง / แผนติดตาม', 'หลังเผยแพร่ ทีมวางแผนติดตามยอดรับชม อัตราดูจบ และการมีส่วนร่วม พร้อมอ่านความคิดเห็นและสำรวจว่าความเข้าใจเรื่องบูรพานิยมเปลี่ยนไปอย่างไร', '#203b54', 'ประโยชน์และผลลัพธ์ที่คาดว่าจะเกิดขึ้น'],
  ['tide', 'The Long Tide', 'เมื่อภาพจำไหลไปตามกระแสสื่อ', 'ภาพแทนทางวัฒนธรรม', 'ภาพจีนในสื่อเปลี่ยนไปตามยุคและมุมมองของผู้เล่า ก่อนส่งต่อเรื่องเกี่ยวกับประเทศหรือวัฒนธรรมอื่น ลองดูว่าเรื่องนั้นเลือกให้เราเห็นอะไรและยังมีหลักฐานจากมุมไหนให้ตรวจสอบอีก', '#424f50', 'สรุป'],
  ['war', 'A Quiet War', 'อ่านหลักฐานเบื้องหลังภาพจำ', 'หนังสือ / รายงาน / สถิติ', 'รวมงานอ่านเรื่องบูรพานิยมและภาพลักษณ์จีนในสายตาตะวันตก พร้อมแหล่งข้อมูลเศรษฐกิจเซินเจิ้นและสำมะโนประชากรจีนที่รายงานใช้อ้างอิง', '#6a5442', 'เอกสารอ้างอิง']
];
```

Merge the original overview into the Red Door foreword. Follow it with the report’s chapters 1–3, then the historical and contemporary parts of chapter 4, and finish with chapters 5–9. Use continuous Thai narrative as the reading text. Fold concrete evidence and context from the source into the narrative, including economic and census figures, clip timings, and the evaluation plan. Keep the complete bibliography in the last book. Make the URLs in chapter 9 clickable. Preserve the report’s attribution of the Shenzhen GDP figure to China Daily (2025), the population proportions to the 2020 census, and the distinction between completed outputs and expected evaluation results.

## Media and precise crop inputs

Preload all four transparent WebP sheets with `Image` objects. Render both faces directly from the sheets. Preserve the original illustrations, printed VHS titles, and cardboard texture without text overlays. Use the same unaltered cover crop for the detail poster.

```js
const SHEET = {
  covers: ['https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20261029_010644_837e04ca-2418-45c1-b8e0-0233265c4cd5.png&w=1744&q=85', 1744, 2336],
  spines: ['https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20261029_010738_a3e47ead-18f2-4974-9468-06d16a25edc5.png&w=2688&q=85', 2688, 1152],
  fix: ['https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20261029_010831_3ebb874b-93dc-433e-87ed-6299aba720f0.png&w=1520&q=85', 1520, 2688],
  fix2: ['https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20261029_092020_f96bc094-db7b-46de-9298-074a24e0a3b8.png&w=1520&q=85', 1520, 2688]
};
const CROP = {
  'spine-bluehour': ['spines',492,31,189,1089], 'cover-bluehour': ['covers',914,72,342,659],
  'spine-river': ['fix',197,54,324,2566], 'cover-river': ['covers',1332,72,344,659],
  'spine-summer': ['spines',937,31,188,1089], 'cover-summer': ['covers',74,813,344,676],
  'spine-green': ['spines',1157,31,185,1090], 'cover-green': ['covers',497,815,344,674],
  'spine-noon': ['spines',44,32,184,1088], 'cover-noon': ['covers',74,72,347,659],
  'spine-observer': ['fix2',371,15,349,2655], 'cover-observer': ['covers',915,815,342,675],
  'spine-birds': ['spines',1573,31,183,1089], 'cover-birds': ['covers',1331,815,345,675],
  'spine-storm': ['fix2',808,15,347,2656], 'cover-storm': ['covers',74,1571,345,681],
  'spine-tide': ['spines',2012,31,188,1089], 'cover-tide': ['covers',496,1577,343,678],
  'spine-war': ['spines',2236,31,189,1089], 'cover-war': ['covers',913,1579,343,676],
  'spine-door': ['spines',2462,31,188,1089], 'cover-door': ['covers',1331,1579,344,677]
};
```

For crop `[x,y,w,h]` on sheet `[W,H]`, use `background-size: (W/w*100)% (H/h*100)%` and `background-position: (x/(W-w)*100)% (y/(H-h)*100)%`. For the SVG poster clip an image to 474 × 900 and set its rectangle to `(-x*474/w,-y*900/h,W*474/w,H*900/h)` with `preserveAspectRatio="none"`.

## Typography and palette

Embed these seven faces as WOFF2 data URLs. Use Newsreader optical-size variable 400 regular and 400 italic for Latin serif text, Inter Tight 500–600 for labels, Noto Sans JP 500 for `閉じる` and `開く`, and Noto Serif SC 700 for `中国印象`. Place Noto Serif Thai in the serif stack and Noto Sans Thai in the sans stack. Preserve the SIL Open Font License notice. Use the exact font bytes from the HTML or obtain the faces from these Google Fonts CSS queries.

- `https://fonts.googleapis.com/css2?family=Newsreader:opsz,wght@6..72,400`
- `https://fonts.googleapis.com/css2?family=Newsreader:ital,opsz,wght@1,6..72,400`
- `https://fonts.googleapis.com/css2?family=Inter+Tight:wght@500..600`
- `https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@500`
- `https://fonts.googleapis.com/css2?family=Noto+Serif+SC:wght@700&text=%E4%B8%AD%E5%9B%BD%E5%8D%B0%E8%B1%A1`
- `https://fonts.googleapis.com/css2?family=Noto+Sans+Thai:wght@100..900`
- `https://fonts.googleapis.com/css2?family=Noto+Serif+Thai:wght@100..900`

Set `--paper: #EDEBE6`, `--sheet: #F4F2ED`, `--ink: #141414`, `--muted: #6D6A63`, `--cobalt: #1F3FB0`, `--rule: rgba(20,20,20,.9)` and `--ease: cubic-bezier(.2,.8,.2,1)`. Overlay fixed noninteractive grain at z-index 40 with multiply blend and .55 opacity. Tile a 220 × 220 SVG with fractal noise at base frequency .85, three octaves, stitched edges, and a matrix to warm grey RGB .45/.42/.38 at alpha .22. Use clips, transforms, and masks for reveals.

## Layout and box geometry

- Fix the top utility bar at 84 px high in a three-column grid with 32 px side padding. Set the logo to 22 px over 9 px with a 5 px gap. Use 21 px outlined labels with 8 px horizontal padding and 10.5 px type at weight 600.
- Set tape height `H=min(46vh,31vw)`. Place the shelf 40 px above the tape top with height `H+80px` and perspective 2200 px. Center a zero-size stage and preserve its 3D context.
- Center the 23 px tabs at `50%−H/2−86px` with 11 px side padding and shared borders. Set the cobalt block to the button’s `offsetLeft` and `offsetWidth`. Slide and resize over .6 s, with the text color transitioning for .45 s.
- Position a 42 px outlined cobalt play disc at `W/2−d/2−6px`, `shelfCenter+.36H`, with a paper tint and solid play triangle. Use `smoothstep(max(0,1−3*abs(T−s)))` for its scale and hide it in detail.
- Position the masked caption 30 px below the tape with the original English VHS title at 31 px, the Thai content heading in cobalt, and the report section name at 11 px, such as “การค้นคว้าและการวิเคราะห์”, spaced 9 px. Put 44 px arrow buttons at `50%+H/2+40px` and 20 px from the sides. Draw the 18 × 10 left arrow with `M5 1L1 5l4 4M1 5h16` and stroke 1.2. Mirror it for next. Set footer insets at 32 px and 26 px above the bottom edge.

Measure `H` with a hidden CSS probe. Set `ws=H*142/840`, `d=H*474/900` and `gap=.03H`. Make three copies of the 11 chapters. Each tape is a zero-size button with a spine of width `ws` at `translateZ(d/2)` and a cover of width `d` at `rotateY(90deg) translateZ(ws/2)`. Center both faces, use 2 px corners and hide their backfaces. The cover shadow is `0 30px 60px -28px rgba(20,16,10,.55)`.

## Motion and input

Run one `requestAnimationFrame` loop. Clamp `dt` to 50 ms and update `s += (T−s)*(1−exp(−k*dt))`, with `k=5.2` normally and `k=18` during drag. Snap at `abs(T−s)<.0001`. Wrap `r=v−s` into `[−16.5,16.5)` and rebase the scroll and target by multiples of 33 beyond four complete strips.

Set `x=r*(ws+gap)+(d−ws+1.6*gap)*B(r)`. Use `B(r)=(r+sin(pi*r)/pi)/2` for `abs(r)<1` and `sign(r)/2` elsewhere. Cull beyond `W/2+1.5d`. Let `o=smoothstep(max(0,1−abs(r)))`. Apply `translate3d(x,H*(−.025o−.045lift),.2oH) rotateZ(−4.5o) rotateX(tiltX*o) rotateY((−90+tiltY)*o)` with angles in degrees. Use `round(100−4abs(r))` for stacking, `.55o` for spine darkness and `.5(1−o)` for cover darkness. Ease hovered neighboring spines toward lift 1 at `1−exp(−12dt)`.

The cover region is within `.55d` of the horizontal center and `.55H` of the shelf’s vertical center, with `abs(T−s)<.3` and no drag or detail. In that region yaw targets `9*(mx−W/2)/(.55d)` and pitch targets `−6*(my−shelfCenter)/(H/2)`. Outside it yaw targets `5*(mx−W/2)/W` and pitch targets 0. Ease both at `1−exp(−7dt)`. Animate captions at `round(s) mod 11` through intermediate titles. Overlap old and new spans inside three clipped rows and slide them from/to ±105% over 650 ms with the paper ease.

A spine click selects that visible tape and a center click opens detail. Arrow buttons and Left/Right step by one. Category jumps use shortest circular distance. Wheel uses the dominant axis scaled by `.5/(ws+gap)` and a 160 ms snap debounce. Begin drag after 5 px, capture the pointer, set `T=T0−dx/(ws+gap)`, snap at release, and suppress the resulting click. Allow horizontal touch drag with `touch-action: pan-y`. Enter on body opens the active tape. Escape closes it.

## Cursor and detail reveal

Use a fixed 58 px fine-pointer cursor at z-index 100. Follow the mouse at `1−exp(−16dt)`. Draw a 1.5 px ring and 6 px dot. Scale the ring to .72 over spines and .55 over buttons, hiding the dot over buttons. In the cover region fill the ring cobalt, scale it to 1.75, hide the dot and reveal `OPEN / 開く` in white. Transition ring transform .5 s, colors .4 s, dot .4 s and label .45 s.

The paper dialog has z-index 60, two equal columns, a 4vw gap, 7vw left and 6vw right padding, and an 84 px logo band with the close button at x=32, y=31. The left stack has 18 px spacing, the original VHS title in cobalt, a `clamp(40px,5.4vw,84px)` Thai serif content heading, muted metadata, 17 px synopsis, 15 px italic credit and 44 px outlined read button. Center the 474:900 poster in the right column. The read control opens the Thai narrative and focuses its heading. Set the prose in a centered book-width column, with the current report section name above the heading and the “ก่อนหน้า” and “ถัดไป” buttons below the text. The Red Door detail, the project button, and the footer credits button open the same foreword and roster above the merged opening part. Show the same report section name in the detail metadata and foreword. Use the section names directly, without numbering. Use the existing paper expansion on opening it.

Use the cover’s projected rectangle for the opening clip inset, a 3 px corner radius and a −4.5° rotation about its center. Animate to a full-screen straight sheet over 1050 ms with `cubic-bezier(.76,0,.18,1)`. Slide the text from `translateY(110%)` to 0 over 900 ms with delays of `620+75i` ms. On close, animate from the current paper frame to the cover rectangle over 850 ms and clear the animations. Use the Web Animations API for the sheet and text.

Use seven SVG mask circles with `(cx,cy,delay-ms)` values `(150,330,0)`, `(340,600,120)`, `(250,120,220)`, `(90,760,300)`, `(400,250,360)`, `(260,860,420)`, `(230,470,180)`. Use mask area `−200 −200 874 1300`. The group uses fractal noise at .011, three octaves and seed 7, then a displacement map at scale 120 using R/G. After 520 ms plus each delay, grow the corresponding radius to 720 over 1250 ms with `1−(1−p)^3` inside the existing frame loop.

## Responsive behavior and accessibility

At widths up to 767 px use `H=min(60vw,40svh)`, a 64 px bar, 16 px sides, 17 px and 7.5 px logo lines, 9 px labels, and hide the top-right course label. Use 7 px tab padding, a 24 px caption title, arrows 6 px from the edges, and the footer 18 px from the bottom. Use a one-column scrolling detail with the poster first at 46svh, 22 px side padding, a 24 px gap and a 42 px title. Keep close at x=16, y=21. Show the custom cursor on fine pointers.

Use semantic buttons, named navigation and shelf regions, a polite chapter announcement and a dialog with `aria-modal` and `aria-labelledby`. Keep background controls inert while detail is open. Move focus to the close button on opening and back to the opener on closing. Hide illustrative faces and the poster from screen readers. Under reduced motion snap shelf and hover changes, replace caption text directly, use 1 ms detail animation durations with zero delays, and reveal the full poster immediately.

Verify the opening tape, wrapping, wheel, drag, keyboard, spine and cover hit targets, tab block, rapid caption changes, cursor states, expanded report, reference links, mobile layout and reduced motion. Deliver the standalone HTML used as the visual reference.
