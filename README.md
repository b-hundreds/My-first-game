# TODO List: Phát triển Game Roguelite 2.5D (Phong cách Dead Cells) bằng ThreeJS

## I. Nền tảng & Thiết lập cơ bản (ThreeJS)

- [ ] Tạo `THREE.Scene` cơ bản.
- [ ] Thiết lập `THREE.WebGLRenderer` và gắn vào HTML canvas.
- [ ] **Camera (Rất quan trọng):**
    - [ ] Quyết định loại Camera: `OrthographicCamera` hay `PerspectiveCamera` (FOV thấp).
    - [ ] Nếu dùng `PerspectiveCamera`, triển khai script theo dõi nhân vật (trục X/Y) giữ khoảng cách cố định.
    - [ ] Nếu dùng `OrthographicCamera`, cấu hình các tham số cho phù hợp.
- [ ] **Ánh sáng:**
    - [ ] Thiết lập ánh sáng cơ bản (`DirectionalLight`, `AmbientLight`).
    - [ ] Cấu hình đổ bóng (`castShadow`, `receiveShadow` cho các đối tượng liên quan).
    - [ ] (Tùy chọn) Thêm ánh sáng đặc biệt (`PointLight`, `SpotLight`).
- [ ] **Game Loop:**
    - [ ] Tạo vòng lặp game ổn định dùng `requestAnimationFrame`.
    - [ ] Triển khai quản lý Delta Time.
- [ ] **Physics Engine (Rất quan trọng):**
    - [ ] Chọn thư viện vật lý (Rapier.js, Cannon-es, Ammo.js).
    - [ ] Tích hợp thư viện vật lý vào dự án.
    - [ ] Tạo các "body" vật lý cho: Nhân vật, Kẻ địch, Nền đất, Vật thể tương tác.
    - [ ] Đồng bộ hóa vị trí/xoay giữa `THREE.Mesh` và Physics Body.
    - [ ] Thiết lập va chạm (collision detection).
    - [ ] Thiết lập nhóm va chạm (collision groups).
- [ ] **Input Handler:**
    - [ ] Tạo hệ thống lắng nghe và xử lý input (Bàn phím / Gamepad).
- [ ] **Asset Loader:**
    - [ ] Tạo hệ thống tải tài nguyên (Models - GLTF, Textures, Audio, Data - JSON).
    - [ ] Sử dụng các Loader tương ứng (`GLTFLoader`, `TextureLoader`, `AudioLoader`).
    - [ ] Hiển thị màn hình loading trong khi tải tài nguyên.

## II. Nhân vật chính (Player Character - "The Beheaded")

- [ ] **Model & Animation:**
    - [ ] Tạo hoặc import Model 3D cho nhân vật chính.
    - [ ] Rigging model (nếu cần).
    - [ ] Tạo hoặc import các Animations cần thiết (Idle, Run, Jump, Roll, Attack, Hurt, Death...).
    - [ ] Tích hợp `THREE.AnimationMixer` để quản lý và chuyển đổi animation.
- [ ] **Player Controller (Script):**
    - [ ] Xử lý input để điều khiển di chuyển (Trái/Phải).
    - [ ] Triển khai logic Nhảy (có thể cả Double Jump).
    - [ ] Triển khai logic Né/Lộn (Roll/Dodge).
    - [ ] Triển khai khoảng thời gian bất tử (i-frames) khi Né.
    - [ ] Triển khai logic Tương tác môi trường (Leo thang, Mở cửa, Nhặt đồ).
    - [ ] Xây dựng State Machine quản lý trạng thái nhân vật.
- [ ] **Physics Body:**
    - [ ] Gắn và cấu hình Physics Body (vd: Capsule Collider) cho nhân vật.
- [ ] **Stats & State:**
    - [ ] Định nghĩa và quản lý chỉ số (HP, tốc độ, sát thương...).
    - [ ] Định nghĩa và quản lý tiền tệ (Cells, Gold).
    - [ ] Theo dõi trạng thái hiện tại (đang tấn công, né, bị choáng...).

## III. Kẻ địch (Enemies)

- [ ] Thiết kế các loại kẻ địch khác nhau (hình dáng, stats, hành vi).
- [ ] **Model & Animation:**
    - [ ] Tạo/Import Model 3D cho từng loại kẻ địch.
    - [ ] Tạo/Import Animations cho kẻ địch (Idle, Patrol, Detect, Attack, Hurt, Death...).
    - [ ] Tích hợp `AnimationMixer` cho kẻ địch.
- [ ] **AI (Trí tuệ nhân tạo):**
    - [ ] Xây dựng State Machine cơ bản cho AI (Idle, Patrol, Chase, Attack, Flee?).
    - [ ] Triển khai logic phát hiện người chơi (Tầm nhìn/Nghe).
    - [ ] (Nâng cao) Triển khai Pathfinding (vd: A*) nếu level phức tạp.
    - [ ] Thiết kế và triển khai các kiểu tấn công (Attack Patterns) riêng biệt.
    - [ ] Triển khai thời gian "telegraph" (báo hiệu) trước tấn công.
- [ ] **Physics Body & Hitboxes:**
    - [ ] Gắn Physics Body cho kẻ địch.
    - [ ] Thiết lập Hitbox (vùng nhận sát thương) và Hurtbox (vùng gây sát thương khi tấn công).
- [ ] **Drops:**
    - [ ] Triển khai logic rơi đồ (Cells, Gold, Vật phẩm) khi kẻ địch bị tiêu diệt.

## IV. Môi trường & Level Design

- [ ] **Procedural Generation (Cốt lõi):**
    - [ ] Chọn thuật toán sinh level (Room-based, BSP, Cellular Automata...).
    - [ ] Triển khai thuật toán để tạo cấu trúc level ngẫu nhiên.
    - [ ] Định nghĩa các Biomes (theme hình ảnh, kẻ địch, cấu trúc riêng).
    - [ ] Tạo các "Room Templates" (nếu dùng phương pháp Room-based).
    - [ ] Triển khai logic đặt (Placement) kẻ địch, bẫy, item một cách có quy tắc.
- [ ] **Level Assets:**
    - [ ] Tạo/Import các khối (Tiles/Modules) 3D để xây dựng level (Nền, Tường, Cầu thang...).
    - [ ] Tạo/Import các vật thể trang trí (Props).
    - [ ] Tạo/Import các loại Bẫy.
- [ ] **Parallax Background:**
    - [ ] Tạo các lớp ảnh nền (background layers).
    - [ ] Triển khai hiệu ứng parallax scrolling dựa trên vị trí camera.
- [ ] **Tương tác môi trường:**
    - [ ] Triển khai Cửa (thường, khóa, phá được).
    - [ ] Triển khai Thang leo.
    - [ ] Triển khai Teleporters.
    - [ ] Triển khai Công tắc, Đòn bẩy.
    - [ ] Triển khai Nền tảng có thể phá hủy.

## V. Hệ thống Gameplay

- [ ] **Combat System:**
    - [ ] Triển khai Hit Detection (Phát hiện va chạm vũ khí/kỹ năng với đối tượng).
    - [ ] Triển khai Damage Calculation (Tính sát thương dựa trên stats, affixes, crit...).
    - [ ] Triển khai Status Effects (Bleed, Burn, Poison, Slow, Stun...).
    - [ ] Triển khai Knockback.
    - [ ] Triển khai i-frames khi nhận sát thương.
- [ ] **Item/Weapon System:**
    - [ ] Thiết kế và triển khai hệ thống vũ khí đa dạng (Loại, Model).
    - [ ] Triển khai hệ thống chỉ số (Stats) và hiệu ứng phụ (Affixes) ngẫu nhiên cho vũ khí.
    - [ ] Triển khai hệ thống độ hiếm (Rarity).
    - [ ] Thiết kế và triển khai hệ thống Kỹ năng phụ trợ (Skills) với cooldown.
- [ ] **Progression System:**
    - [ ] Triển khai hệ thống tiến trình trong lượt chơi (Nhặt đồ, Scrolls of Power).
    - [ ] Triển khai hệ thống tiến trình vĩnh viễn (Meta-progression):
        - [ ] Thu thập Cells.
        - [ ] Tạo NPC Collector và giao diện nâng cấp.
        - [ ] Triển khai mở khóa vũ khí/kỹ năng mới (thêm vào pool đồ rơi).
        - [ ] Triển khai nâng cấp vĩnh viễn (Flask charges, Gold save...).
        - [ ] Triển khai mở khóa Trang phục (Cosmetic).
        - [ ] Triển khai hệ thống Runes (Metroidvania abilities).
- [ ] **Economy:**
    - [ ] Triển khai logic quản lý Cells và Gold (nhận, tiêu, mất khi chết).
- [ ] **Hub Area:**
    - [ ] Thiết kế và xây dựng khu vực Hub ban đầu.
    - [ ] Đặt các NPC/Chức năng meta-progression vào Hub.

## VI. Vật phẩm & Trang bị (Items & Equipment)

- [ ] Tạo Model 3D cho các loại Vũ khí khác nhau.
- [ ] Tạo Model 3D và/hoặc hiệu ứng hình ảnh (VFX) cho các Kỹ năng.
- [ ] Thiết kế và triển khai hệ thống Bùa/Đột biến (Amulets/Mutations).
- [ ] Triển khai vật phẩm Bình máu (Health Flask).
- [ ] Triển khai vật phẩm Chìa khóa (Keys).
- [ ] Triển khai vật phẩm Cuộn giấy sức mạnh (Scrolls).

## VII. Giao diện người dùng (UI)

- [ ] Quyết định phương pháp triển khai UI (HTML/CSS Overlay hoặc In-World UI).
- [ ] **HUD (Heads-Up Display):**
    - [ ] Hiển thị Thanh máu.
    - [ ] Hiển thị Số lượng Cells/Gold.
    - [ ] Hiển thị Vũ khí/Kỹ năng đang trang bị (+ Cooldown).
    - [ ] Hiển thị Số lượng bình máu.
    - [ ] Hiển thị Trạng thái (Buff/Debuffs).
- [ ] **Menus:**
    - [ ] Tạo Menu chính.
    - [ ] Tạo Menu tạm dừng.
    - [ ] Tạo Màn hình Inventory/Equipment.
    - [ ] Tạo Màn hình lựa chọn Mutations.
    - [ ] Tạo Màn hình Bản đồ.
    - [ ] Tạo Giao diện NPC Collector (Nâng cấp vĩnh viễn).
    - [ ] Tạo Màn hình Game Over/Death.
    - [ ] Tạo Màn hình chuyển cảnh/Loading.
- [ ] **World UI:**
    - [ ] Hiển thị số sát thương (Damage Numbers).
    - [ ] Hiển thị Tên/Máu kẻ địch.
    - [ ] Hiển thị biểu tượng phát hiện (!).
    - [ ] Hiển thị biểu tượng tương tác.
- [ ] Triển khai UI đã chọn theo phương pháp đã quyết định.

## VIII. Âm thanh & Âm nhạc (Audio)

- [ ] **Sound Effects (SFX):**
    - [ ] Thu thập hoặc tạo SFX cho: Bước chân, Nhảy, Lộn, Vung vũ khí, Va chạm (Hit), Kỹ năng, Kẻ địch, Nhặt đồ, Môi trường, UI.
    - [ ] Tích hợp SFX vào các hành động tương ứng.
- [ ] **Background Music (BGM):**
    - [ ] Thu thập hoặc sáng tác BGM cho: Biomes, Combat, Hub, Bosses, Menus.
    - [ ] Tích hợp BGM và logic chuyển nhạc (vd: khi vào combat).
- [ ] **Implementation:**
    - [ ] Tạo một `AudioManager` sử dụng Web Audio API để quản lý và phát âm thanh.

## IX. Hiệu ứng hình ảnh (Visual Effects - VFX)

- [ ] **Particle Systems:**
    - [ ] Tích hợp thư viện Particle hoặc tự tạo hệ thống cơ bản.
    - [ ] Tạo hiệu ứng particle cho: Đánh trúng (sparks), Máu, Trạng thái, Kỹ năng, Nhặt đồ, Bụi (chạy, nhảy, đáp).
- [ ] **Trails:**
    - [ ] Tạo hiệu ứng vệt sáng vũ khí (Weapon Trails).
    - [ ] Tạo hiệu ứng vệt mờ khi né (Dodge Trails).
- [ ] **Screen Effects:**
    - [ ] Triển khai Rung màn hình (Screen Shake).
    - [ ] Triển khai hiệu ứng màn hình khi thấp máu.
- [ ] **Shaders (GLSL):**
    - [ ] (Nâng cao) Viết shader tùy chỉnh cho vật liệu, ánh sáng, post-processing nếu cần.

## X. Công cụ & Quy trình (Tools & Workflow)

- [ ] (Rất nên có) Phát triển hoặc tìm kiếm Level Editor để tạo Room Templates/Level cơ bản.
- [ ] Thiết lập quy trình làm việc (Asset Pipeline) rõ ràng cho việc tạo và nhập tài sản.
- [ ] Tạo các công cụ Debugging (Hiển thị colliders, trạng thái AI, stats...). Sử dụng các `Helpers` của ThreeJS.
- [ ] Thiết lập và sử dụng hệ thống quản lý phiên bản (Version Control) như Git.
