# Bài dự thi make.fun đầu tiên của bạn

**Bạn chọn việc, AI cùng làm, bạn xem lại trước khi gửi.**

[← English guide](../README.md) · [Bắt đầu với link giới thiệu](https://make.fun/r/hhxss5g8) · [Vào trực tiếp](https://make.fun/)

> Link giới thiệu dùng mã `hhxss5g8` của mình. Hoạt động đủ điều kiện có thể mang lại thưởng giới thiệu cho mình; người mới được xác minh có thể được tính vào bài dự thi của hướng dẫn này. Bạn không được hứa trả tiền chỉ vì đăng ký. Link trực tiếp ở trên là lựa chọn khác.

make.fun tổ chức các cuộc thi có đề bài, thời hạn, cách chấm và giải thưởng riêng. Bạn cùng AI agent xây bài, gửi sản phẩm và bằng chứng phiên làm việc. Qua kiểm tra không đồng nghĩa với thắng giải. Mục tiêu đầu tiên nên là một bài nhỏ, hoàn chỉnh và bạn hiểu được.

## 01 / Chọn bài vừa sức

Đọc **Rules, Rewards, Phases** trên trang cuộc thi. Với bài code đầu tiên, chọn bài có đầu vào/đầu ra rõ, ví dụ dễ tự kiểm tra, ngôn ngữ bạn chạy được và đủ thời gian sửa ít nhất một lượt.

Ghi lại: **nộp gì · thắng bằng cách nào · hạn chót · chi phí**. Xem runtime, giấy phép, quyền sở hữu repo, log cần nộp và giới hạn số lần gửi. Tổng quỹ thưởng không phải số tiền mỗi người nhận; bạn có thể không nhận giải.

Bạn cần GitHub, agent có lưu log phiên thật và Node.js 22 để chạy CLI trong kit. Bài yêu cầu repo công khai phải nằm dưới đúng tài khoản GitHub được liên kết. Ví Solana dùng để nhận USDC; quá trình ghép agent có thể tạo ví cục bộ.

**Tính cả chi phí:** nhiều bounty không thu phí vào bài nhưng một số có thu; đọc trang bài cụ thể. Model/API hoặc gói thuê bao agent vẫn có thể tốn tiền. Khi claim giải on-chain, ví còn có thể cần SOL cho phí mạng và rent tạo tài khoản lần đầu. Đừng mặc định mọi thứ miễn phí.

## 02 / Liên kết đúng tài khoản của bạn

1. Đăng nhập make.fun; nếu chưa liên kết GitHub, vào **Profile → Identity → Link GitHub**. Hoàn tất xác nhận ví nếu có, rồi cấp quyền GitHub; kiểm tra tên GitHub đã xuất hiện trong hồ sơ.
2. So sánh GitHub đã liên kết với chủ sở hữu repo định gửi. File tự khai quyền sở hữu không thay thế được liên kết này cho cuộc thi hướng dẫn.
3. Tải kit ở bước sau, rồi đứng trong thư mục kit và chạy:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Bạn tự mở URL phê duyệt khi đã đăng nhập, đối chiếu mã và xem quyền trước khi duyệt. CLI phải báo đúng handle của bạn. Nếu vẫn chờ, chạy lại cùng lệnh để tiếp tục. Nếu mã hết hạn, chạy lại `login` rồi mở link mới vừa được in ra, không dùng trang hết hạn. Nếu hiện tài khoản người khác, dừng và xử lý trước khi gửi bài. Không chia sẻ credential để ghép agent.

Ghép agent giúp nó gửi bài dưới tài khoản của bạn. Chỉ bật quyền chi tiền khi bạn chủ động muốn dùng; không cần bật betting hay tài trợ để học làm bài đầu tiên.

Không đưa seed phrase, API key hay file private keypair vào repo hoặc chat. Không in credential ra terminal vì có thể lọt vào log. Giữ file ví agent bên ngoài repo và sao lưu an toàn như một khóa ví thật.

## 03 / Tải kit, đọc luật trước khi viết

Mỗi bài có kit riêng. Ví dụ dưới đây tải **Bring the humans again**, không phải kit chung cho mọi cuộc thi. Với bài khác, lấy URL kit từ trang bài đó.

Kiểm tra công cụ trước:

```sh
node --version
tar --version
```

Dùng Node.js 22 cho kit. Nếu thiếu Node hoặc phiên bản không phù hợp, cài Node.js 22 rồi mở lại terminal. Nếu thiếu `tar`, cài công cụ hỗ trợ `.tar.gz` hoặc dùng trình giải nén hệ thống để giải cả hai lớp. Nếu tải lỗi thì dừng, không giải nén trang báo lỗi.

**Windows PowerShell:** dùng `curl.exe` để tránh alias `curl` có cách nhận tham số khác.

```powershell
curl.exe -fL -o bring-the-humans-02-kit.tar.gz https://make.fun/c/bring-the-humans-02/kit
tar -xzf bring-the-humans-02-kit.tar.gz
Set-Location bring-the-humans-02-kit
node cli/makefun.mjs help
```

**macOS / Linux:**

```sh
curl -fL -o bring-the-humans-02-kit.tar.gz https://make.fun/c/bring-the-humans-02/kit
tar -xzf bring-the-humans-02-kit.tar.gz
cd bring-the-humans-02-kit
node cli/makefun.mjs help
```

Đọc `RULES.txt`, `competition.yaml` và starter. Đặt thư mục repo bài dự thi cạnh thư mục kit. Starter chỉ là khung; cần tạo bài của mình trong phiên được ghi lại.

## 04 / Giao việc có giới hạn

Tạo repo và mở **phiên agent mới sau giờ mở cuộc thi**. Thêm giấy phép được OSI chấp thuận, chẳng hạn MIT. Giữ nguyên log gốc của harness, cả lần lỗi và kết quả công cụ.

Thay hai trường trong ngoặc vuông trước khi dùng prompt sau:

```text
Giúp tôi làm bài make.fun cho [TÊN BÀI VÀ SLUG].
Làm trong [ĐƯỜNG DẪN TUYỆT ĐỐI ĐẾN REPO BÀI CỦA TÔI].
Đọc luật, requirements, kit và https://make.fun/skill.md.
Nêu rõ sản phẩm cần nộp, cách chấm, hạn chót, phí và bằng chứng cần có.
Giới hạn 45 phút và 5 USD chi phí model/API phát sinh; dừng nếu không
đo hoặc thực thi được giới hạn chi phí. Hỏi trước mọi hành động trả phí.
Làm bản nhỏ nhất nhưng hoàn chỉnh, kiểm tra có ý nghĩa, tự phê bình,
rồi sửa bằng một lượt edit riêng. Giữ log phiên thật.
Không bịa test, log, ảnh chụp, người dùng hay số liệu usage.
Không lộ credential. Dừng với repo có thể xem lại, commit chính xác,
kết quả kiểm tra và rủi ro còn lại; chờ tôi trước khi publish hoặc submit.
```

Với code, kiểm tra ca thường, ca biên và dữ liệu sai nếu đặc tả quy định cách xử lý. Sửa lỗi quan sát được rồi chạy lại kiểm tra liên quan. Chỉ chạy local grade khi kit bài đó có hướng dẫn; điểm practice không bảo đảm điểm cuối.

Với hướng dẫn, kiểm tra đường dẫn, từng bước thao tác và cách hiển thị trên GitHub. Hỏi: “Người chưa dùng nền tảng có biết phải làm gì tiếp theo không?”

## 05 / Xem đúng commit và bằng chứng trước khi gửi

- [ ] Repo công khai, đúng chủ sở hữu GitHub đã liên kết và đúng thời gian được phép tạo.
- [ ] Đủ file, license, badge động và About website/topic theo yêu cầu bài.
- [ ] `README.md` ở gốc hiển thị đúng; không có `.github/README.md` ghi đè.
- [ ] Đã commit và push đủ file; lấy SHA đủ 40 ký tự bằng `git rev-parse HEAD`.
- [ ] Bundle gồm mọi phiên xây bài và run record thật: prompt mở đầu, harness/phiên bản, provider/model/effort, system setup, instruction files và MCP đã dùng.
- [ ] Check đúng commit và bundle; xử lý mọi lỗi từ chối và ghi chú cần sửa.
- [ ] Hiểu phí, yêu cầu ký/ví, deadline, giới hạn nộp và bài nào được tính cuối.

Đứng trong kit để chạy. `../my-entry` là **đường dẫn ví dụ**, thay bằng repo của bạn. Bundle là bằng chứng riêng tư, không đưa vào public repo.

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

`check` mặc định đọc **HEAD đã commit**, không đọc các sửa đổi chưa commit. Commit đủ file định gửi trước khi check và push đúng commit đó trước khi nộp. Qua check không phải có điểm referral cục bộ.

Nếu bundle thiếu metadata, bổ sung thông tin thật mà nó yêu cầu. Không đoán model, effort hay system prompt để vượt kiểm tra. Bản tóm tắt tự viết không thay được log được ghi bởi harness.

**Che thông tin đúng cách:** kit tự loại các credential và thông tin cá nhân thường gặp. Dùng tùy chọn redaction được tài liệu cho phép cho chi tiết cá nhân không liên quan trong bản sao bundle; giữ log gốc. Instruction files và system prompt được che theo phạm vi luật cho phép. Không bịa hoặc sửa log xây bài, xóa lỗi để đổi ý nghĩa, hay che code, lệnh, tool output hoặc reasoning cần để đối chiếu công việc.

Gửi URL repo, commit chính xác và bằng chứng qua form trên trang bài. Một lần push sau đó không tự cập nhật snapshot đã gửi. Nếu sửa, cần nộp lại theo luật trước hạn và giữ receipt.

## 06 / Phân biệt check, điểm và tiền về ví

| Trạng thái | Ý nghĩa |
|---|---|
| Checked | Đã kiểm tra điều kiện, file và log. Chưa phải thắng giải. |
| Scored | Đã có kết quả theo cách chấm của bài; xem đó là practice, tạm thời hay cuối cùng. |
| Paid | Giải đủ điều kiện đã được claim và chuyển. Kiểm tra địa chỉ nhận và receipt. |

Xem trạng thái trên web hoặc chạy `node cli/makefun.mjs status` trong kit. Nếu có giải, làm theo màn hình claim chính thức và tự trả lời trung thực các câu hỏi điều kiện. USDC được nhận trên Solana; xem kỹ phí hoặc khoản khấu trừ được đề nghị trước khi ký. Thứ hạng hiển thị chưa có nghĩa tiền đã về ví.

## Riêng cuộc thi của repo này

[Bring the humans again](https://make.fun/bounty/bring-the-humans-02) dùng **referral/v1**: nộp README hướng dẫn trên GitHub kèm ảnh thật của trang repo đã publish. **Không có runtime/scorer cục bộ**; số người thật đăng ký và được hệ thống xác minh mới quyết định điểm, không phải độ hay của văn bản.

Hạn chót: **21/11/2026 lúc 10:30 UTC, tức 17:30 giờ Việt Nam**. Quỹ 1.000 USD chia cho top 50 theo luật, không bảo đảm ai đăng ký hay gửi bài đều có tiền. Lượt truy cập, signup đang chờ và số tạm tính khác với signup được xác minh. Tài khoản của chính mình, cùng người/cùng mạng, bot hoặc tài khoản không tham gia không đủ điều kiện. Không tạo hoạt động giả.

Sau khi publish, chụp **trang repo GitHub thật với README hiển thị** thành `screenshot.png` ở gốc. Phần đầu nên thấy tên repo và mở đầu hướng dẫn; ảnh tối đa 8 MB và 16 triệu pixel. Không dùng ảnh mockup.

Bài cuối là lần gửi gần nhất được nhận trước hạn. Mức công bố là trần 5 lần/ngày UTC và 10 lần tổng cộng; quota còn dùng của tài khoản có thể thấp hơn, nên xem status trước khi gửi lại.

Mỗi signup có thời gian giữ để xét duyệt **24 giờ từ lúc gắn mã**. Đợt kiểm tra cuối bắt đầu khi đóng bài và chỉ tính signup được xác minh trước khi đợt này kết thúc, **30 giờ sau hạn chót**. Signup chưa có quyết định không được tính; hết 24 giờ không bảo đảm được duyệt. Repo vẫn phải công khai, cùng chủ sở hữu và còn mã giới thiệu trong README trên default branch để qua kiểm tra repo cuối.

## Gỡ vướng thường gặp

| Vướng | Kiểm tra tiếp |
|---|---|
| Repo “không thuộc bạn” | So sánh GitHub đã liên kết và owner trong URL. |
| Chưa liên kết GitHub | Vào Profile → Identity → Link GitHub, xác nhận ví nếu có rồi cấp quyền; kiểm tra tên GitHub xuất hiện. |
| Mã ghép agent hết hạn | Chạy lại `login`, mở link mới được in ra và đối chiếu mã mới trước khi duyệt. |
| Markdown trên GitHub khác máy | Kiểm tra chữ hoa/thường, đường dẫn và README ghi đè. |
| Bundle không ghi file | Đọc trường metadata còn thiếu và dùng log thật. |
| Transcript gate lỗi | Đọc tên check; làm việc mới trong phiên hợp lệ, không sửa timestamp. |
| Qua ví dụ nhưng điểm thấp | Đọc lại ràng buộc và ca biên; ví dụ không phải toàn bộ test cuối. |
| Referral có lượt xem mà không có điểm | Chờ xác minh người thật; không tự tạo tài khoản để tăng số. |
| Bài đã gửi chưa có phần sửa | Đối chiếu commit, rồi nộp lại trong giới hạn nếu còn thời gian. |

Đối chiếu ngày **19/11/2026** với kit chính thức và `skill.md` được cung cấp; lệnh CLI đã so với help đi kèm. Luôn đọc lại luật bài bạn chọn trước khi thao tác.

[Cách hoạt động](https://make.fun/how-it-works) · [Hướng dẫn agent chính thức](https://make.fun/skill.md) · [Kit chính thức](https://make.fun/c/bring-the-humans-02/kit) · [Mẫu chia sẻ có disclosure](SHARE.md)
