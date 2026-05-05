# ĐỀ THI HỌC KỲ MÔN: KNOWLEDGE GRAPHS

**Mã đề: KG-01**
**Thời gian: 90 phút**
**Được sử dụng tài liệu**

---

## Câu 1: Kiến trúc và Nguyên lý (Lý thuyết hệ thống) (2.0 điểm)

**a)** Trình bày kiến trúc phân tầng của Semantic Web (Semantic Web Layer Cake / Technology Stack) dựa trên tài liệu. Hãy giải thích vai trò của từng tầng từ Unicode/URI lên đến SPARQL.

**b)** Phân tích 4 nguyên tắc cơ bản của Linked Data (Linked Open Data) theo Tim Berners-Lee. Mô hình 5 sao (Five Star Scheme) đánh giá mức độ “mở” và “liên kết” của dữ liệu như thế nào?

**c)** So sánh sự khác biệt cốt yếu giữa Web truyền thống (Classic Web / Web of Documents) và Web ngữ nghĩa (Semantic Web / Web of Data) dựa trên các khía cạnh: đối tượng định danh, khả năng xử lý của máy tính, và mục đích truy vấn.

---

## Câu 2: Mô hình hóa dữ liệu với RDF và Serialization (2.5 điểm)

Cho đoạn mô tả sau về một viện bảo tàng và các tác phẩm nghệ thuật:

> **Viện bảo tàng MOMA (Museum of Modern Art) có địa chỉ tại 11 West 53rd Street, New York. MOMA sở hữu tác phẩm “The Starry Night” của họa sĩ Vincent van Gogh. Tác phẩm này được sáng tác năm 1889, thuộc thể loại hậu ấn tượng (Post-Impressionism). Ngoài ra, MOMA còn trưng bày tác phẩm “The Persistence of Memory” của Salvador Dalí, sáng tác năm 1931, thể loại siêu thực (Surrealism).**

**Yêu cầu:**

**a)** Biểu diễn các thông tin trên thành các bộ ba RDF (Subject, Predicate, Object). Sử dụng các URI tùy ý nhưng phải nhất quán. Gợi ý: sử dụng namespace cho museum, artist, artwork.

**b)** Viết lại các bộ ba đó dưới định dạng **Turtle** (có khai báo @prefix) và định dạng **JSON-LD**.

**c)** Mô tả đồ thị RDF (bằng lời hoặc vẽ sơ đồ ASCII) tương ứng với các bộ ba trên. Chỉ rõ các node là URI hay literal, và các cạnh là property gì.

---

## Câu 3: Ngôn ngữ truy vấn SPARQL (2.0 điểm)

Giả sử có một knowledge graph về các trường đại học với các lớp và thuộc tính như sau (biểu diễn dạng Turtle mô phỏng):

```turtle
@prefix : <http://example.org/univ/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

:MIT rdf:type :University ; :name "Massachusetts Institute of Technology" ; :established 1861 .
:Stanford rdf:type :University ; :name "Stanford University" ; :established 1885 .
:UCBerkeley rdf:type :University ; :name "University of California, Berkeley" ; :established 1868 .
:CS_dept rdf:type :Department ; :name "Computer Science" ; :belongsTo :MIT .
:EE_dept rdf:type :Department ; :name "Electrical Engineering" ; :belongsTo :MIT .
:AI_lab rdf:type :Lab ; :name "AI Lab" ; :partOf :CS_dept .
:ProfSmith rdf:type :Professor ; :name "John Smith" ; :worksAt :CS_dept ; :researchArea "Artificial Intelligence" .
:ProfJones rdf:type :Professor ; :name "Mary Jones" ; :worksAt :EE_dept ; :researchArea "Robotics" .
```

**Yêu cầu:** Viết các truy vấn SPARQL sau:

**a)** Truy vấn SELECT để lấy tên tất cả các giáo sư (Professor) làm việc tại khoa (Department) thuộc về MIT, đồng thời lấy cả tên khoa. Sử dụng FILTER để chỉ lấy giáo sư có researchArea chứa từ "Intelligence" (không phân biệt chữ hoa/thường). Dùng OPTIONAL để lấy thêm email nếu có (giả sử có property :email).

**b)** Truy vấn CONSTRUCT tạo ra một đồ thị mới chứa tất cả các cặp (university, professor) trong đó professor làm việc tại một khoa thuộc về university. Kết quả CONSTRUCT sử dụng predicate mới :employs.

**c)** Giải thích ý nghĩa của GROUP BY và HAVING trong SPARQL. Cho một ví dụ (không cần code) minh họa việc đếm số lượng giáo sư theo researchArea và chỉ lấy các nhóm có số lượng lớn hơn 1.

---

## Câu 4: Thiết kế Ontology và Logic mô tả (1.5 điểm)

**a)** Thiết kế một ontology nhỏ cho lĩnh vực **thư viện số** bao gồm:
- Ít nhất 3 lớp (Class): ví dụ `Book`, `Author`, `Library`
- Ít nhất 2 thuộc tính đối tượng (Object Property): ví dụ `wrote`, `locatedIn`
- Ít nhất 1 thuộc tính kiểu dữ liệu (Data Property): ví dụ `publicationYear`

Hãy mô tả bằng RDFS/OWL (có thể dùng cú pháp Turtle hoặc giải thích bằng lời) và chỉ rõ domain và range cho mỗi property.

**b)** Chuyển câu tự nhiên sau sang ký hiệu của Description Logic (ALC hoặc SHOIN, tùy chọn): *“Mọi cuốn sách viết về chủ đề “Toán học” đều có ít nhất một tác giả là giáo sư.”* (Giả sử có các khái niệm: `Book`, `Topic`, `Professor`, vai trò `hasTopic`, `hasAuthor`).

**c)** Xác định đặc tính của các property sau (Transitive, Symmetric, Inverse, Functional) và giải thích ngắn:
- `hasParent` (có tính bắc cầu không? có tính đối xứng không?)
- `isMarriedTo` (có tính đối xứng không? có tính functional không?)
- `hasStudentID` (có tính functional không?)

---

## Câu 5: Suy luận (Reasoning) và Thế giới mở (OWA) (2.0 điểm)

**a)** Áp dụng các quy tắc suy diễn của RDFS (RDF Schema) cho các dữ kiện và lược đồ sau. Hãy liệt kê TẤT CẢ các triple mới có thể suy ra được (giải thích theo từng bước):

```turtle
:hasParent rdfs:domain :Person .
:hasParent rdfs:range :Person .
:hasParent rdfs:subPropertyOf :hasAncestor .
:Grandparent rdfs:subClassOf :Person .
:John :hasParent :Mary .
```

**b)** Xem xét ontology sau (trong OWL):

```turtle
:City owl:disjointWith :Country .
:Berlin rdf:type :City .
:Berlin rdf:type :Country .
```

Hãy giải thích tại sao ontology này **inconsistent** (không nhất quán) theo nguyên lý của OWL DL. Nếu áp dụng Open World Assumption (OWA) và Non-unique Name Assumption (NUNA), liệu điều gì khác biệt so với Closed World Assumption (CWA) trong các hệ cơ sở dữ liệu quan hệ?

**c)** So sánh hai giả định: Open World Assumption (OWA) trong RDF/Semantic Web và Closed World Assumption (CWA) trong cơ sở dữ liệu quan hệ. Dùng ví dụ cụ thể từ tài liệu để minh họa sự khác biệt khi trả lời câu hỏi “Peter có bao nhiêu con?” khi chỉ biết `:Peter :fatherOf :Julia , :Mary .`

---

# ĐÁP ÁN – ĐỀ KG-01

## Câu 1: Kiến trúc và Nguyên lý

**a) Kiến trúc phân tầng của Semantic Web**

Dựa trên tài liệu (02_RDF.pdf trang 7, 03_RDFS trang 4, 05_SPARQL trang 6, 06_OWL trang 5, 09-OWL2 trang 3), kiến trúc Semantic Web thường được mô tả như một “chiếc bánh nhiều tầng” (Layer Cake). Các tầng chính (từ dưới lên):

1. **Unicode / URI** (tầng cơ sở): 
   - **Unicode** đảm bảo biểu diễn ký tự của mọi ngôn ngữ (tài liệu 01_Intro trang 31-32).
   - **URI** (Uniform Resource Identifier) dùng để định danh duy nhất mọi tài nguyên (trang 54-55). URIs có thể là URLs (dereferenceable).
2. **XML** (eXtensible Markup Language): Cung cấp cú pháp chung để trao đổi dữ liệu, nhưng không mang ngữ nghĩa (trang 34-44).
3. **RDF** (Resource Description Framework): Mô hình dữ liệu đồ thị dạng triple (subject, predicate, object). Đây là cốt lõi của Semantic Web (02_RDF trang 8-10).
4. **RDFS** (RDF Schema): Cho phép định nghĩa lớp (class), phân cấp lớp (subClassOf), thuộc tính (property), miền (domain) và tập (range) – mang một phần ngữ nghĩa (03_RDFS trang 21-25).
5. **OWL** (Web Ontology Language): Mở rộng RDFS, thêm các cấu trúc phức tạp: ràng buộc cardinality, disjointness, property characteristics (transitive, symmetric, inverse, functional) (06_OWL trang 6-12). OWL2 bổ sung profiles (EL, RL, QL) (09-OWL2 trang 11-13).
6. **SPARQL**: Ngôn ngữ truy vấn cho RDF. Cho phép pattern matching trên đồ thị (05_SPARQL trang 9-10).
7. **Rules / Logic** (các tầng trên cùng): Suy luận logic, chữ ký số, bằng chứng, tin cậy (trust) – được nhắc đến nhưng không đi sâu trong các bài giảng đầu.

**b) Bốn nguyên tắc Linked Data và mô hình 5 sao**

- **Bốn nguyên tắc Linked Data** (theo Tim Berners-Lee, 2006, được nhắc trong 04_LOD trang 53-54):
  1. Sử dụng URI để đặt tên cho mọi thứ.
  2. Sử dụng HTTP URI để mọi người có thể tra cứu (dereferenceable).
  3. Khi một URI được tra cứu, cung cấp thông tin hữu ích bằng các chuẩn (RDF, SPARQL,…).
  4. Bao gồm các liên kết (link) tới các URI khác để phát hiện thêm dữ liệu.

- **Mô hình 5 sao** (tài liệu 04_LOD trang 16, 55):
  - ★: Dữ liệu có sẵn trên web với giấy phép mở (any license).
  - ★★: Dữ liệu ở dạng cấu trúc máy đọc được (ví dụ Excel thay vì ảnh scan).
  - ★★★: Dùng định dạng không độc quyền (non-proprietary format), ví dụ CSV.
  - ★★★★: Dùng chuẩn W3C (RDF) kèm URIs để định danh.
  - ★★★★★: Tất cả những điều trên **cộng với** liên kết tới các tập dữ liệu khác (links to other datasets) để tạo thành một web dữ liệu thực sự.

**c) So sánh Web truyền thống và Web ngữ nghĩa**

Dựa trên 01_Intro trang 13-17:

| Khía cạnh | Classic Web (Web of Documents) | Semantic Web (Web of Data) |
|-----------|--------------------------------|----------------------------|
| Đối tượng định danh | Tài liệu (HTML, PDF, ảnh) qua URL | Mọi thực thể (entity) như người, địa danh, tổ chức qua URI |
| Khả năng xử lý của máy | Máy chỉ hiểu cú pháp (layout, link), không hiểu ngữ nghĩa; tìm kiếm dựa trên từ khóa, gặp vấn đề với từ đồng nghĩa, đa nghĩa. | Dữ liệu có cấu trúc và ngữ nghĩa (RDF), máy có thể “hiểu” và suy luận. Hỗ trợ truy vấn phức tạp theo đặc tả. |
| Mục đích truy vấn | Tìm tài liệu chứa từ khóa; khó trả lời câu hỏi chính xác như “Bác sĩ ở Smalltown có lịch làm chiều thứ Tư” (trang 16). | Truy vấn thực thể và quan hệ; có thể trả lời câu hỏi chính xác dựa trên dữ liệu liên kết (ví dụ Google Knowledge Graph). |

---

## Câu 2: Mô hình hóa dữ liệu với RDF và Serialization

**a) Bộ ba RDF (ví dụ sử dụng các prefix)**

Giả sử:
- `@prefix museum: <http://example.org/museum/>`
- `@prefix artist: <http://example.org/artist/>`
- `@prefix artwork: <http://example.org/artwork/>`
- `@prefix xsd: <http://www.w3.org/2001/XMLSchema#>`

Các triple:

1. `museum:MOMA rdf:type museum:Museum .`
2. `museum:MOMA museum:address "11 West 53rd Street, New York" .`
3. `museum:MOMA museum:owns artwork:StarryNight .`
4. `artwork:StarryNight rdf:type artwork:Painting .`
5. `artwork:StarryNight artwork:creator artist:VanGogh .`
6. `artwork:StarryNight artwork:year "1889"^^xsd:integer .`
7. `artwork:StarryNight artwork:genre "Post-Impressionism" .`
8. `museum:MOMA museum:owns artwork:PersistenceMemory .`
9. `artwork:PersistenceMemory rdf:type artwork:Painting .`
10. `artwork:PersistenceMemory artwork:creator artist:Dali .`
11. `artwork:PersistenceMemory artwork:year "1931"^^xsd:integer .`
12. `artwork:PersistenceMemory artwork:genre "Surrealism" .`
13. `artist:VanGogh rdf:type artist:Painter .`
14. `artist:VanGogh artist:name "Vincent van Gogh" .`
15. `artist:Dali rdf:type artist:Painter .`
16. `artist:Dali artist:name "Salvador Dali" .`

(Chú ý: Có thể thêm triple về artist, nhưng nội dung đoạn văn chỉ cung cấp tên của họ, do đó khai báo tên là đủ.)

**b) Định dạng Turtle**

```turtle
@prefix museum: <http://example.org/museum/> .
@prefix artist: <http://example.org/artist/> .
@prefix artwork: <http://example.org/artwork/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

museum:MOMA a museum:Museum ;
    museum:address "11 West 53rd Street, New York" ;
    museum:owns artwork:StarryNight, artwork:PersistenceMemory .

artwork:StarryNight a artwork:Painting ;
    artwork:creator artist:VanGogh ;
    artwork:year "1889"^^xsd:integer ;
    artwork:genre "Post-Impressionism" .

artwork:PersistenceMemory a artwork:Painting ;
    artwork:creator artist:Dali ;
    artwork:year "1931"^^xsd:integer ;
    artwork:genre "Surrealism" .

artist:VanGogh a artist:Painter ;
    artist:name "Vincent van Gogh" .

artist:Dali a artist:Painter ;
    artist:name "Salvador Dali" .
```

**Định dạng JSON-LD** (theo 02_RDF trang 23, JSON-LD 1.1 là chuẩn W3C)

```json
{
  "@context": {
    "museum": "http://example.org/museum/",
    "artist": "http://example.org/artist/",
    "artwork": "http://example.org/artwork/",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#"
  },
  "@graph": [
    {
      "@id": "museum:MOMA",
      "@type": "museum:Museum",
      "museum:address": "11 West 53rd Street, New York",
      "museum:owns": [{"@id": "artwork:StarryNight"}, {"@id": "artwork:PersistenceMemory"}]
    },
    {
      "@id": "artwork:StarryNight",
      "@type": "artwork:Painting",
      "artwork:creator": {"@id": "artist:VanGogh"},
      "artwork:year": {"@value": 1889, "@type": "xsd:integer"},
      "artwork:genre": "Post-Impressionism"
    },
    {
      "@id": "artwork:PersistenceMemory",
      "@type": "artwork:Painting",
      "artwork:creator": {"@id": "artist:Dali"},
      "artwork:year": {"@value": 1931, "@type": "xsd:integer"},
      "artwork:genre": "Surrealism"
    },
    {
      "@id": "artist:VanGogh",
      "@type": "artist:Painter",
      "artist:name": "Vincent van Gogh"
    },
    {
      "@id": "artist:Dali",
      "@type": "artist:Painter",
      "artist:name": "Salvador Dali"
    }
  ]
}
```

**c) Mô tả đồ thị RDF**

Đồ thị có 5 node chính là các URI: `museum:MOMA`, `artwork:StarryNight`, `artwork:PersistenceMemory`, `artist:VanGogh`, `artist:Dali`. Ngoài ra có các literal (chuỗi, số nguyên).

- Node `museum:MOMA` có liên kết `rdf:type` đến `museum:Museum` (một URI, node loại class). Nó có cạnh `museum:address` tới literal, và hai cạnh `museum:owns` lần lượt tới hai node artwork.
- Mỗi node artwork có cạnh `rdf:type` tới `artwork:Painting`, cạnh `artwork:creator` tới node artist tương ứng, cạnh `artwork:year` tới literal integer, cạnh `artwork:genre` tới literal string.
- Mỗi node artist có `rdf:type` tới `artist:Painter` và `artist:name` tới literal string.

Không có blank node trong ví dụ này. Đồ thị có hướng, các literal chỉ có cạnh đi vào.

---

## Câu 3: Ngôn ngữ truy vấn SPARQL

**a) Truy vấn SELECT với FILTER và OPTIONAL**

```sparql
PREFIX : <http://example.org/univ/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT ?profName ?deptName ?email
WHERE {
  ?prof rdf:type :Professor .
  ?prof :name ?profName .
  ?prof :worksAt ?dept .
  ?dept :name ?deptName .
  ?dept :belongsTo :MIT .
  ?prof :researchArea ?area .
  FILTER( regex(?area, "Intelligence", "i") )
  OPTIONAL { ?prof :email ?email . }
}
```

*Giải thích:* Biến `?prof` duyệt qua các Professor, `?dept` là Department mà professor làm việc, `?dept :belongsTo :MIT`. FILTER sử dụng regex với flag "i" cho case-insensitive. OPTIONAL lấy email nếu có, không có thì ?email bị unbound.

**b) Truy vấn CONSTRUCT**

```sparql
PREFIX : <http://example.org/univ/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

CONSTRUCT {
  ?univ :employs ?prof .
}
WHERE {
  ?prof rdf:type :Professor .
  ?prof :worksAt ?dept .
  ?dept :belongsTo ?univ .
  ?univ rdf:type :University .
}
```

*Giải thích:* CONSTRUCT tạo ra các triple mới với predicate `:employs` từ university đến professor. WHERE xác định mối quan hệ professor → department → university.

**c) GROUP BY và HAVING trong SPARQL**

- **GROUP BY** được dùng để nhóm các kết quả theo một hoặc nhiều biến. Sau khi group, các hàm tổng hợp như `COUNT`, `SUM`, `AVG`, `MIN`, `MAX` có thể áp dụng lên từng nhóm.
- **HAVING** được sử dụng sau GROUP BY để lọc các nhóm dựa trên điều kiện của hàm tổng hợp (không thể dùng WHERE vì WHERE lọc từng dòng trước khi group).

*Ví dụ (không yêu cầu code):* Đếm số lượng giáo sư theo researchArea, sau đó chỉ giữ lại các nhóm có số lượng lớn hơn 1.

```
SELECT ?area COUNT(?prof) AS ?count
WHERE { ?prof :researchArea ?area }
GROUP BY ?area
HAVING (?count > 1)
```

Điều này tương tự mệnh đề HAVING trong SQL.

---

## Câu 4: Thiết kế Ontology và Logic mô tả

**a) Ontology thư viện số (RDFS/OWL)**

Các lớp:
- `Book`
- `Author`
- `Library`

Object properties:
- `wrote`: domain `Author`, range `Book`. (Một tác giả viết sách)
- `locatedIn`: domain `Library`, range `Location` (có thể thêm lớp Location, nhưng ở đây tạm coi range là `xsd:string` hoặc lớp riêng). Để đơn giản, xem `locatedIn` là object property với range `City`.

Data property:
- `publicationYear`: domain `Book`, range `xsd:integer`.

Biểu diễn bằng Turtle/RDF:

```turtle
@prefix : <http://example.org/library/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

:Book rdf:type rdfs:Class .
:Author rdf:type rdfs:Class .
:Library rdf:type rdfs:Class .
:City rdf:type rdfs:Class .

:wrote rdf:type rdf:Property ;
    rdfs:domain :Author ;
    rdfs:range :Book .

:locatedIn rdf:type rdf:Property ;
    rdfs:domain :Library ;
    rdfs:range :City .

:publicationYear rdf:type rdf:Property ;
    rdfs:domain :Book ;
    rdfs:range xsd:integer .
```

**b) Chuyển câu tự nhiên sang Description Logic**

Câu: *“Mọi cuốn sách viết về chủ đề “Toán học” đều có ít nhất một tác giả là giáo sư.”*

Giả sử các khái niệm (concepts) và vai trò (roles):
- `Book` : Sách
- `Topic` : Chủ đề
- `Professor` : Giáo sư
- `hasTopic` : vai trò (sách – có chủ đề)
- `hasAuthor` : vai trò (sách – có tác giả)

Câu trên có thể viết:  
`Book ⊓ (∃ hasTopic.{Mathematics}) ⊑ ∃ hasAuthor.Professor`

Trong đó `{Mathematics}` là cá thể (nominal) của Topic. Ở ALC không có nominal, nhưng có thể dùng `∃ hasTopic.Mathematics` nếu coi `Mathematics` là một concept (lớp con của Topic). Tuy nhiên chính xác hơn, dùng SHIQ/SHOIN cho phép nominal. Ở cấp độ ALC có thể viết:  
`Book ⊓ ∃ hasTopic.Topic ⊓ (∀ hasTopic.(Topic → Mathematics))` nhưng dài.

Với SHIN (có nominal): `Book ⊓ (∃ hasTopic.{Mathematics}) ⊑ ∃ hasAuthor.Professor`.

**c) Đặc tính của property**

- `hasParent`:
  - Không có tính bắc cầu (transitive) vì bố của bố là ông, nhưng `hasParent` thường không được định nghĩa là transitive (nếu transitive, từ A hasParent B và B hasParent C suy ra A hasParent C – sai). Tuy nhiên theo tài liệu 06_OWL, `ancestor` là transitive, còn `hasParent` có thể dùng để định nghĩa property chain (09-OWL2 trang 9-10).
  - Không đối xứng (symmetric) vì nếu A là bố của B thì B không thể là bố của A.
- `isMarriedTo`:
  - Có tính đối xứng (symmetric): nếu A kết hôn với B thì B kết hôn với A. (tài liệu 06_OWL trang 18 có `sitsOppositeOf` là symmetric; tương tự `isMarriedTo` cũng vậy)
  - Không functional (một người có thể kết hôn nhiều lần? Trong đa số xã hội hiện đại, một thời điểm chỉ kết hôn với một người, nhưng nếu xét toàn bộ cuộc đời, có thể có nhiều hơn một. OWL cho phép khai báo `FunctionalProperty` nếu muốn ràng buộc mỗi subject chỉ có tối đa một object. `isMarriedTo` thường không được khai báo functional).
- `hasStudentID`:
  - Có tính functional (mỗi sinh viên có duy nhất một mã số). Theo 06_OWL trang 24-25: `FunctionalProperty` nghĩa là "there can only be one". `hasStudentID` là datatype property và có thể khai báo functional.

---

## Câu 5: Suy luận và Thế giới mở

**a) Suy diễn RDFS**

Từ các triple đã cho:

1. `:John :hasParent :Mary .`
2. `:hasParent rdfs:domain :Person .`
3. `:hasParent rdfs:range :Person .`
4. `:hasParent rdfs:subPropertyOf :hasAncestor .`
5. `:Grandparent rdfs:subClassOf :Person .`

Áp dụng các quy tắc suy diễn RDFS (tài liệu 03_RDFS trang 38 - bảng deduction rules):

- **Rule rdfs2** (domain): `<s p o>` và `p rdfs:domain c` ⇒ `<s rdf:type c>`.  
  Với `s = :John, p = :hasParent, c = :Person` ⇒ `:John rdf:type :Person`.

- **Rule rdfs3** (range): `<s p o>` và `p rdfs:range c` ⇒ `<o rdf:type c>`.  
  Với `o = :Mary, c = :Person` ⇒ `:Mary rdf:type :Person`.

- **Rule rdfs7** (subPropertyOf): `p1 rdfs:subPropertyOf p2` và `<s p1 o>` ⇒ `<s p2 o>`.  
  `:hasParent rdfs:subPropertyOf :hasAncestor` và `:John :hasParent :Mary` ⇒ `:John :hasAncestor :Mary`.

- **Rule rdfs9** (subClassOf): `<s rdf:type c1>` và `c1 rdfs:subClassOf c2` ⇒ `<s rdf:type c2>`.  
  Ở đây không có `:Grandparent rdfs:subClassOf :Person` kết hợp với ai. Nếu có `:someone rdf:type :Grandparent` thì ta suy ra `:someone rdf:type :Person`. Nhưng trong dữ kiện không có, nên không suy thêm.

Kết luận: Các triple mới suy ra là:
- `:John rdf:type :Person`
- `:Mary rdf:type :Person`
- `:John :hasAncestor :Mary`

**b) Inconsistency trong OWL**

Ontology:
```turtle
:City owl:disjointWith :Country .
:Berlin rdf:type :City .
:Berlin rdf:type :Country .
```

`owl:disjointWith` có nghĩa là hai lớp không có phần tử chung (giao bằng rỗng). `:Berlin` vừa là `:City` vừa là `:Country`, tức là nằm trong giao của hai lớp. Điều này mâu thuẫn với axiom disjointness. Trong OWL DL, lý luận (reasoner) sẽ phát hiện mâu thuẫn và kết luận ontology **inconsistent** (không có mô hình nào thỏa mãn). Hệ quả: từ một ontology inconsistent, mọi câu đều có thể suy ra (nguyên lý "ex falso quodlibet").

So sánh với CWA trong CSDL quan hệ: Không có khái niệm disjointness ngầm, nhưng nếu ta có bảng City và bảng Country, một bản ghi không thể đồng thời nằm trong cả hai bảng (vì thực thể được xác định bởi khóa chính). Hơn nữa, CWA giả định những gì không được biết là sai. OWA giả định những gì không được biết có thể đúng hoặc sai.

**c) So sánh OWA và CWA**

- **Open World Assumption (OWA)**: Trong Semantic Web, nếu một sự kiện không có mặt trong knowledge graph, ta không thể kết luận nó sai. Sự kiện đó có thể đúng nhưng chưa được ghi nhận. (Tài liệu 02_RDF trang 32-33)
- **Closed World Assumption (CWA)**: Trong cơ sở dữ liệu quan hệ (và nhiều hệ thống truyền thống), nếu một sự kiện không có trong cơ sở dữ liệu, ta coi nó là sai (negation as failure).

*Ví dụ:* Biết `:Peter :fatherOf :Julia , :Mary .`

- **CWA (cơ sở dữ liệu)**: Nếu chỉ có hai bộ cha-con đó, hệ thống kết luận Peter có **đúng 2** người con. Bất kỳ ai khác không xuất hiện trong bảng đều không phải con của Peter.
- **OWA (RDF)**: Peter có ít nhất hai người con, nhưng có thể có nhiều hơn (vì không khẳng định được là không còn ai khác). Ngoài ra, liệu `:Julia` và `:Mary` có chắc chắn là hai người khác nhau không? Non-unique name assumption: có thể `:Julia` và `:Mary` là cùng một người nếu có `owl:sameAs`. Do đó, từ hai triple trên, ta không thể suy ra số lượng con chính xác. (Tài liệu 02_RDF trang 31-34).

Điều này dẫn đến các chiến lược suy luận khác nhau: OWA yêu cầu xử lý cẩn thận với absent information, và thường đi kèm với lý luận không đơn điệu (non-monotonic) trong các ứng dụng thực tế.


# ĐỀ THI HỌC KỲ MÔN: KNOWLEDGE GRAPHS

**Mã đề: KG-02**
**Thời gian: 90 phút**
**Được sử dụng tài liệu**

---

## Câu 1: Kiến trúc và Nguyên lý (2.0 điểm)

**a)** Giải thích mối quan hệ giữa các tầng Unicode/URI, XML, RDF, RDFS, OWL và SPARQL trong kiến trúc Semantic Web. Tầng nào cung cấp khả năng “formal semantics” mạnh nhất? Dựa vào tài liệu, hãy chỉ ra hai hạn chế của RDF Schema (RDFS) mà OWL giải quyết được.

**b)** Linked Open Data (LOD) yêu cầu “dereferencable URIs” và “RDF links to other datasets”. Hãy giải thích tại sao `owl:sameAs` thường bị lạm dụng và nên dùng các giải pháp thay thế nào (theo tài liệu).

**c)** Phân tích câu nói của Google: “Things, not strings”. Liên hệ với sự khác biệt giữa tìm kiếm truyền thống dựa trên từ khóa và tìm kiếm dựa trên knowledge graph. Cho ví dụ cụ thể về từ đồng nghĩa/đa nghĩa minh họa.

---

## Câu 2: Mô hình hóa dữ liệu với RDF và Serialization (2.5 điểm)

Cho đoạn mô tả sau về một hãng hàng không và các chuyến bay:

> **Hãng hàng không “Vietnam Airlines” (mã IATA: VN) có trụ sở chính tại 200 Nguyễn Sơn, Hà Nội. Hãng khai thác chuyến bay VN123 từ Hà Nội (HAN) đi TP. Hồ Chí Minh (SGN) vào lúc 08:30 ngày 2025-05-10. Chuyến bay này sử dụng máy bay Airbus A321, có sức chứa 180 hành khách. Phi công chỉ huy là Nguyễn Văn A (bằng lái A320/A321). Hành khách Trần Thị B đặt vé hạng Phổ thông (Economy) cho ghế 14A.**

**Yêu cầu:**

**a)** Biểu diễn thông tin trên thành các bộ ba RDF. Sử dụng các URI tự định nghĩa, phù hợp và nhất quán (ví dụ: `airline:`, `flight:`, `airport:`, `pilot:`, `passenger:`).

**b)** Viết lại dữ liệu dưới định dạng **Turtle** (có @prefix) và **RDF/XML** (có thể trình bày dạng cây hoặc tag, nhưng cần hợp lệ).

**c)** Mô tả đồ thị RDF bằng lời: chỉ ra các node nào là URI, node nào là blank node (nếu có), node nào là literal. Vẽ sơ đồ đơn giản bằng ký tự ASCII.

---

## Câu 3: Ngôn ngữ truy vấn SPARQL (2.0 điểm)

Xét knowledge graph về hệ thống trường học với dữ liệu mẫu (dạng Turtle):

```turtle
@prefix : <http://example.org/school/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

:SchoolA rdf:type :School ; :name "Nguyen Du Secondary School" .
:SchoolB rdf:type :School ; :name "Le Loi High School" .
:Class9A rdf:type :Class ; :className "9A" ; :belongsTo :SchoolA .
:Class9B rdf:type :Class ; :className "9B" ; :belongsTo :SchoolA .
:Class10A rdf:type :Class ; :className "10A" ; :belongsTo :SchoolB .
:Student1 rdf:type :Student ; :name "Minh" ; :studiesIn :Class9A ; :age 14 .
:Student2 rdf:type :Student ; :name "Lan" ; :studiesIn :Class9A ; :age 14 ; :email "lan@example.com" .
:Student3 rdf:type :Student ; :name "Hoa" ; :studiesIn :Class9B ; :age 15 .
:Student4 rdf:type :Student ; :name "Long" ; :studiesIn :Class10A ; :age 16 .
:TeacherA rdf:type :Teacher ; :name "Cô Hạnh" ; :teaches :Class9A ; :subject "Math" .
:TeacherB rdf:type :Teacher ; :name "Thầy Nam" ; :teaches :Class9B ; :subject "Physics" .
```

**Yêu cầu:** Viết các truy vấn SPARQL sau:

**a)** Truy vấn SELECT: lấy tên học sinh (Student) có tuổi từ 14 đến 15, học tại trường “Nguyen Du Secondary School”. Kết quả gồm tên học sinh, tên lớp, và tuổi. Sử dụng OPTIONAL để lấy email nếu có.

**b)** Truy vấn CONSTRUCT: tạo ra đồ thị mới mô tả quan hệ “dạy bởi” giữa mỗi lớp và giáo viên. Sử dụng predicate mới `:taughtBy`.

**c)** Giải thích sự khác biệt giữa `FILTER NOT EXISTS` và `MINUS` trong SPARQL. Với dữ liệu trên, hãy viết một ví dụ truy vấn tìm các lớp không có giáo viên nào (nêu rõ kết quả mong đợi).

---

## Câu 4: Thiết kế Ontology và Logic mô tả (1.5 điểm)

**a)** Thiết kế một ontology nhỏ cho lĩnh vực **bất động sản** (real estate). Bao gồm:
- 4 lớp: `Building`, `Apartment`, `Person`, `Agency`
- 2 object property: `locatedIn` (Building → Location), `rentedBy` (Apartment → Person)
- 1 object property có tính inverse: `owns` (Person → Building) và `ownedBy` là inverse.
- 1 data property: `price` (Apartment → xsd:decimal)

Hãy trình bày bằng RDFS/OWL (cú pháp Turtle hoặc lời) và chỉ rõ domain, range, characteristic (nếu có).

**b)** Chuyển câu sau thành Description Logic (dùng ALC hoặc SHOIN):  
*“Mọi căn hộ được cho thuê bởi một người không phải là chủ sở hữu của tòa nhà chứa căn hộ đó.”*  
(Giả sử có roles: `rentedBy`, `ownerOf`, `containedIn`; concepts: `Apartment`, `Person`, `Building`.)

**c)** Xác định các đặc tính (Transitive, Symmetric, InverseFunctional, Functional) cho các property sau, dựa trên hiểu biết từ OWL:
- `hasBiologicalMother` (có InverseFunctional không? Functional không?)
- `hasSameFingerprintAs` (có Symmetric không? Transitive không?)
- `hasSSN` (Social Security Number) – Xét trên tập người Mỹ.

---

## Câu 5: Suy luận và Thế giới mở (2.0 điểm)

**a)** Áp dụng quy tắc suy diễn RDFS (từ bảng trong tài liệu) cho các triple sau. Liệt kê tất cả các triple mới suy ra được.

```turtle
:Vehicle rdf:type rdfs:Class .
:Car rdfs:subClassOf :Vehicle .
:hasWheels rdfs:domain :Vehicle .
:hasWheels rdfs:range xsd:integer .
:hasWheels rdfs:subPropertyOf :hasPart .
:myCar a :Car .
:myCar :hasWheels "4"^^xsd:integer .
```

**b)** Xét ontology OWL nhỏ:

```turtle
:Parent owl:equivalentClass [ owl:intersectionOf ( :Person [a owl:Restriction ; owl:onProperty :hasChild ; owl:minCardinality "1"^^xsd:integer ] ) ] .
:Person owl:disjointWith :Robot .
:John a :Parent .
```

Liệu ontology này có nhất quán không? Nếu có, hãy chứng minh John là Person? Nếu thêm triple `:John a :Robot` thì điều gì xảy ra? Giải thích theo nguyên lý của OWL reasoner.

**c)** Lấy ví dụ từ tài liệu về “AAA principle” (Anyone can say Anything about Anything). Kết hợp với Open World Assumption và Non-unique Name Assumption, hãy giải thích tại sao trong Semantic Web không thể kết luận “Barcelona không phải là thủ đô của Tây Ban Nha” chỉ từ câu “Madrid là thủ đô của Tây Ban Nha” mà cần thêm ràng buộc `owl:FunctionalProperty` và `owl:differentFrom`. (Tham khảo 06_OWL trang 28-29).

---

# ĐÁP ÁN – ĐỀ KG-02

## Câu 1: Kiến trúc và Nguyên lý

**a) Mối quan hệ các tầng và hạn chế của RDFS**

- **Unicode/URI** cung cấp định danh và bộ ký tự; **XML** là cú pháp nền; **RDF** là mô hình dữ liệu triple; **RDFS** thêm ngữ nghĩa sơ cấp (lớp, phân cấp, domain/range); **OWL** mở rộng RDFS với logic mạnh hơn; **SPARQL** truy vấn. Tầng có formal semantics mạnh nhất là **OWL DL** (dựa trên Description Logics). (Tài liệu: 02_RDF, 03_RDFS, 06_OWL, 09-OWL2)
- **Hai hạn chế của RDFS mà OWL giải quyết** (03_RDFS trang 47-48, 06_OWL trang 3):
  1. RDFS không thể diễn tả cardinality ràng buộc (ví dụ “mỗi quốc gia có đúng một thủ đô”).
  2. RDFS không thể diễn tả tính disjointness (ví dụ “một thành phố không thể đồng thời là quốc gia”).
  OWL bổ sung các cấu trúc như `owl:cardinality`, `owl:disjointWith`, `owl:FunctionalProperty`, v.v.

**b) Lạm dụng `owl:sameAs` và giải pháp thay thế**

- Tài liệu 04_LOD trang 12: `owl:sameAs` nên dùng để liên kết hai tài nguyên **giống hệt nhau** (cùng một thực thể). Các trường hợp lạm dụng: liên kết một người với trang chủ của họ (khác loại), liên kết một cửa hàng Starbucks với tập đoàn Starbucks, liên kết thành phố Hamburg với bang Hamburg.
- **Giải pháp thay thế** (trang 13):
  - `rdfs:seeAlso` để chỉ ra tài nguyên liên quan (không khẳng định đồng nhất).
  - `foaf:homepage` để liên kết một người với trang web cá nhân.
  - Các property đặc thù miền.

**c) “Things, not strings”**

Tài liệu 01_Intro trang 11: Google chuyển từ tìm kiếm dựa trên từ khóa (strings) sang thực thể (entities) có định danh duy nhất và quan hệ rõ ràng.

- **Tìm kiếm từ khóa**: gặp vấn đề với từ đồng nghĩa (ví dụ “physician” vs “doctor”) và đa nghĩa (ví dụ “Java” có thể là đảo, ngôn ngữ lập trình, hoặc cà phê). Kết quả trả về tài liệu chứa từ khóa, không phân biệt ngữ nghĩa.
- **Tìm kiếm dựa trên KG**: dùng URI cho mỗi thực thể (ví dụ `dbpedia:Java_programming_language`). Câu hỏi “tìm bác sĩ ở Smalltown” sẽ ánh xạ `Smalltown` vào một URI thành phố, `bác sĩ` vào lớp `Physician`, trả về các thực thể có quan hệ `worksIn` với thành phố đó. Máy hiểu ngữ nghĩa nhờ ontology.

---

## Câu 2: Mô hình hóa RDF

**a) Bộ ba RDF (gợi ý)**

Prefixes:
- `@prefix airline: <http://example.org/airline/>`
- `@prefix flight: <http://example.org/flight/>`
- `@prefix airport: <http://example.org/airport/>`
- `@prefix pilot: <http://example.org/pilot/>`
- `@prefix passenger: <http://example.org/passenger/>`
- `@prefix xsd: <http://www.w3.org/2001/XMLSchema#>`

Các triple (liệt kê đầy đủ):
1. `airline:VietnamAirlines rdf:type airline:Airline .`
2. `airline:VietnamAirlines airline:iataCode "VN" .`
3. `airline:VietnamAirlines airline:headquarters "200 Nguyễn Sơn, Hà Nội" .`
4. `flight:VN123 rdf:type flight:Flight .`
5. `flight:VN123 flight:operatedBy airline:VietnamAirlines .`
6. `flight:VN123 flight:departureAirport airport:HAN .`
7. `flight:VN123 flight:arrivalAirport airport:SGN .`
8. `flight:VN123 flight:departureTime "2025-05-10T08:30:00"^^xsd:dateTime .`
9. `flight:VN123 flight:aircraft "Airbus A321" .`
10. `flight:VN123 flight:capacity "180"^^xsd:integer .`
11. `flight:VN123 flight:commandedBy pilot:NguyenVanA .`
12. `pilot:NguyenVanA rdf:type pilot:Pilot .`
13. `pilot:NguyenVanA pilot:name "Nguyễn Văn A" .`
14. `pilot:NguyenVanA pilot:license "A320/A321" .`
15. `passenger:TranThiB rdf:type passenger:Passenger .`
16. `passenger:TranThiB passenger:name "Trần Thị B" .`
17. `passenger:TranThiB passenger:books flight:VN123 .`
18. `passenger:TranThiB passenger:seat "14A" .`
19. `passenger:TranThiB passenger:class "Economy" .`
(Thêm triple cho các sân bay HAN, SGN nếu cần, nhưng đoạn văn không cung cấp tên đầy đủ, chỉ mã. Có thể thêm `airport:HAN rdf:type airport:Airport ; airport:code "HAN" .` tương tự.)

**b) Serialization**

**Turtle** (rút gọn, dùng `;` và `,`):

```turtle
@prefix airline: <http://example.org/airline/> .
@prefix flight: <http://example.org/flight/> .
@prefix airport: <http://example.org/airport/> .
@prefix pilot: <http://example.org/pilot/> .
@prefix passenger: <http://example.org/passenger/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

airline:VietnamAirlines a airline:Airline ;
    airline:iataCode "VN" ;
    airline:headquarters "200 Nguyễn Sơn, Hà Nội" .

flight:VN123 a flight:Flight ;
    flight:operatedBy airline:VietnamAirlines ;
    flight:departureAirport airport:HAN ;
    flight:arrivalAirport airport:SGN ;
    flight:departureTime "2025-05-10T08:30:00"^^xsd:dateTime ;
    flight:aircraft "Airbus A321" ;
    flight:capacity "180"^^xsd:integer ;
    flight:commandedBy pilot:NguyenVanA .

pilot:NguyenVanA a pilot:Pilot ;
    pilot:name "Nguyễn Văn A" ;
    pilot:license "A320/A321" .

passenger:TranThiB a passenger:Passenger ;
    passenger:name "Trần Thị B" ;
    passenger:books flight:VN123 ;
    passenger:seat "14A" ;
    passenger:class "Economy" .

airport:HAN a airport:Airport ; airport:code "HAN" .
airport:SGN a airport:Airport ; airport:code "SGN" .
```

**RDF/XML** (đoạn trích mẫu cho một vài triple, không ghi hết toàn bộ do dài, nhưng đúng cú pháp):

```xml
<?xml version="1.0"?>
<rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
         xmlns:airline="http://example.org/airline/"
         xmlns:flight="http://example.org/flight/"
         xmlns:pilot="http://example.org/pilot/"
         xmlns:passenger="http://example.org/passenger/">
  <rdf:Description rdf:about="http://example.org/airline/VietnamAirlines">
    <rdf:type rdf:resource="http://example.org/airline/Airline"/>
    <airline:iataCode>VN</airline:iataCode>
    <airline:headquarters>200 Nguyễn Sơn, Hà Nội</airline:headquarters>
  </rdf:Description>
  <rdf:Description rdf:about="http://example.org/flight/VN123">
    <rdf:type rdf:resource="http://example.org/flight/Flight"/>
    <flight:operatedBy rdf:resource="http://example.org/airline/VietnamAirlines"/>
    <flight:departureAirport rdf:resource="http://example.org/airport/HAN"/>
    <!-- ... -->
  </rdf:Description>
</rdf:RDF>
```

**c) Mô tả đồ thị RDF**

Đồ thị có các node URI: `airline:VietnamAirlines`, `flight:VN123`, `airport:HAN`, `airport:SGN`, `pilot:NguyenVanA`, `passenger:TranThiB`. Các node literal cho giá trị chuỗi, số, datetime.

Không có blank node trong ví dụ này.

ASCII sơ đồ (chỉ nét chính):

```
[airline:VietnamAirlines] --airline:iataCode--> "VN"
                         --airline:headquarters--> "200 Nguyễn Sơn..."
[flight:VN123] --flight:operatedBy--> [airline:VietnamAirlines]
             --flight:departureAirport--> [airport:HAN]
             --flight:arrivalAirport--> [airport:SGN]
             --flight:departureTime--> "2025-05-10T08:30:00"^^xsd:dateTime
             --flight:commandedBy--> [pilot:NguyenVanA]
[pilot:NguyenVanA] --pilot:name--> "Nguyễn Văn A"
[passenger:TranThiB] --passenger:books--> [flight:VN123]
                    --passenger:seat--> "14A"
```

---

## Câu 3: SPARQL

**a) Truy vấn SELECT**

```sparql
PREFIX : <http://example.org/school/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT ?studentName ?className ?age ?email
WHERE {
  ?student rdf:type :Student .
  ?student :name ?studentName .
  ?student :age ?age .
  FILTER(?age >= 14 && ?age <= 15)
  ?student :studiesIn ?class .
  ?class :className ?className .
  ?class :belongsTo ?school .
  ?school :name "Nguyen Du Secondary School" .
  OPTIONAL { ?student :email ?email . }
}
```

**b) CONSTRUCT**

```sparql
PREFIX : <http://example.org/school/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

CONSTRUCT {
  ?class :taughtBy ?teacher .
}
WHERE {
  ?teacher rdf:type :Teacher .
  ?teacher :teaches ?class .
}
```

**c) `FILTER NOT EXISTS` vs `MINUS`**

- `FILTER NOT EXISTS` kiểm tra một pattern không tồn tại **trong cùng một phạm vi biến**. Nếu pattern tồn tại, dòng bị lọc bỏ.
- `MINUS` thực hiện phép trừ tập hợp: loại bỏ các binding của phía trái nếu tồn tại binding tương thích ở phía phải, nhưng xử lý unbound variables khác nhau (MINUS không loại bỏ nếu biến bên phải unbound).

Ví dụ: Tìm các lớp không có giáo viên nào (dữ liệu hiện tại: cả Class9A và Class9B đều có giáo viên, Class10A không có giáo viên nào trong dữ liệu).

```sparql
SELECT ?class WHERE {
  ?class rdf:type :Class .
  FILTER NOT EXISTS { ?teacher :teaches ?class . }
}
```
Kết quả mong đợi: `:Class10A` (vì không có triple nào khẳng định giáo viên dạy lớp đó).

---

## Câu 4: Thiết kế Ontology và Logic mô tả

**a) Ontology bất động sản (Turtle)**

```turtle
@prefix : <http://example.org/realestate/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix owl: <http://www.w3.org/2002/07/owl#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

:Building rdf:type owl:Class .
:Apartment rdf:type owl:Class .
:Person rdf:type owl:Class .
:Agency rdf:type owl:Class .
:Location rdf:type owl:Class .

:locatedIn rdf:type owl:ObjectProperty ;
    rdfs:domain :Building ;
    rdfs:range :Location .

:rentedBy rdf:type owl:ObjectProperty ;
    rdfs:domain :Apartment ;
    rdfs:range :Person .

:owns rdf:type owl:ObjectProperty ;
    rdfs:domain :Person ;
    rdfs:range :Building .
:ownedBy owl:inverseOf :owns .

:price rdf:type owl:DatatypeProperty ;
    rdfs:domain :Apartment ;
    rdfs:range xsd:decimal .
```

**b) Chuyển sang Description Logic**

Câu: “Mọi căn hộ được cho thuê bởi một người không phải là chủ sở hữu của tòa nhà chứa căn hộ đó.”

Ký hiệu:
- `Apartment` ≡ A
- `Person` ≡ P
- `Building` ≡ B
- `rentedBy` ≡ R (người thuê)
- `ownerOf` ≡ O (quan hệ “là chủ sở hữu của” một tòa nhà)
- `containedIn` ≡ C (căn hộ nằm trong tòa nhà)

Cần diễn đạt: ∀ x ( A(x) → ∃ y ( R(x, y) ∧ P(y) ∧ ¬ ∃ z ( C(x, z) ∧ O(y, z) ∧ B(z) ) ) )

Trong ALC (có thể dùng negation):  
`A ⊑ ∃ R. ( P ⊓ ( ¬ ∃ C. (∃ O⁻. {y}? ) ) )` không trực tiếp. Viết đơn giản:  
`A ⊑ ∃ R. ( P ⊓ ( ∀ C. ¬ O ) )` tạm hiểu là: mỗi căn hộ được cho thuê bởi một người mà người đó không có quan hệ sở hữu với bất kỳ tòa nhà nào chứa căn hộ đó. Cụ thể:  
`A ⊑ ∃ R. ( P ⊓ ( ∀ ownedBuilding.¬ (∃ contains. {x} ) ) )` nhưng phức tạp.

Đáp án chấp nhận: biểu diễn dạng SHIQ với nominal và inverse:  
`Apartment ⊑ ∃ rentedBy. ( Person ⊓ ( ∀ ownerOf⁻. (¬ (∃ contains. {self}) ) ) )` – nhưng trong khuôn khổ đề, sinh viên có thể viết bằng lời logic bậc nhất.

**c) Đặc tính property**

- `hasBiologicalMother`: 
  - InverseFunctional? Có, vì mỗi người chỉ có duy nhất một mẹ ruột (nếu biết mẹ thì suy ra người con). `InverseFunctionalProperty` nghĩa là object xác định duy nhất subject.
  - Functional? Không (một mẹ có thể có nhiều con, không phải functional từ subject sang object).
- `hasSameFingerprintAs`:
  - Symmetric: Có, nếu A có cùng vân tay với B thì B có cùng vân tay với A.
  - Transitive: Có (bắc cầu: A ≡ B và B ≡ C ⇒ A ≡ C).
- `hasSSN`: 
  - Functional: Có (mỗi người Mỹ có đúng một SSN). OWL cho phép khai báo `owl:FunctionalProperty`.

---

## Câu 5: Suy luận và Thế giới mở

**a) Suy diễn RDFS**

Dữ liệu:
1. `:Car rdfs:subClassOf :Vehicle` (triple 2)
2. `:hasWheels rdfs:domain :Vehicle`
3. `:myCar a :Car`
4. `:myCar :hasWheels "4"^^xsd:integer`
5. `:hasWheels rdfs:subPropertyOf :hasPart`

Áp dụng:
- **rdfs9** (subClassOf): `:myCar a :Car` và `:Car rdfs:subClassOf :Vehicle` ⇒ `:myCar a :Vehicle`.
- **rdfs2** (domain): `:myCar :hasWheels "4"` và `:hasWheels rdfs:domain :Vehicle` ⇒ `:myCar a :Vehicle` (đã có).
- **rdfs7** (subPropertyOf): `:hasWheels rdfs:subPropertyOf :hasPart` và `:myCar :hasWheels "4"` ⇒ `:myCar :hasPart "4"`.

Triple suy ra: `:myCar a :Vehicle` (có thể trùng), `:myCar :hasPart "4"^^xsd:integer`.

**b) Tính nhất quán của ontology**

Ontology:
- `Parent ≡ Person ⊓ (≥1 hasChild)`
- `Person ⊓ Robot ≡ owl:Nothing` (disjoint)
- `:John a :Parent`

Suy ra `:John a :Person` (vì là subclass of `Parent` phải là Person). Không có mâu thuẫn. Thêm `:John a :Robot` sẽ gây ra `:John a :Person` và `:John a :Robot` trong khi `Person` và `Robot` disjoint ⇒ inconsistent. OWL reasoner báo lỗi.

**c) AAA + OWA + NUNA**

Tài liệu 06_OWL trang 28: “Barcelona không phải thủ đô Tây Ban Nha” không thể kết luận chỉ từ “Madrid là thủ đô”. Vì AAA cho phép bất kỳ ai nói bất cứ điều gì, và OWA cho phép thông tin chưa biết có thể đúng. Hơn nữa NUNA: Madrid và Barcelona có thể là cùng một thành phố nếu chưa có `owl:differentFrom`.

Để kết luận, cần khai báo:
- `:capitalOf owl:InverseFunctionalProperty` (mỗi quốc gia chỉ có một thủ đô) – từ đó nếu biết Madrid là thủ đô và Barcelona khác Madrid (owl:differentFrom), thì Barcelona không thể là thủ đô.
- Hoặc `:capitalOf owl:FunctionalProperty` (mỗi thành phố chỉ là thủ đô của tối đa một quốc gia) kết hợp với `owl:differentFrom` giữa Tây Ban Nha và Pháp để suy ra Madrid không phải thủ đô Pháp.

Ví dụ này minh họa rõ sự cần thiết của các ràng buộc logic mạnh hơn RDFS.


# ĐỀ THI HỌC KỲ MÔN: KNOWLEDGE GRAPHS

**Mã đề: KG-03**
**Thời gian: 90 phút**
**Được sử dụng tài liệu**

---

## Câu 1: Kiến trúc và Nguyên lý (2.0 điểm)

**a)** Trình bày ngắn gọn kiến trúc “Semantic Web Stack” (Layer Cake) và giải thích tại sao các tầng phía trên (Logic, Proof, Trust) lại ít được triển khai rộng rãi trong thực tế so với các tầng RDF/OWL/SPARQL.

**b)** Phân tích vai trò của **content negotiation** (nội dung thương lượng) trong Linked Data. Dựa vào tài liệu, hãy giải thích hai cách phổ biến để kết hợp RDF và HTML: (1) link tới file RDF riêng, (2) content negotiation. Ưu nhược điểm của mỗi cách.

**c)** Theo tài liệu, DBpedia và YAGO đều được xây dựng từ Wikipedia nhưng có cách tiếp cận khác nhau. Hãy chỉ ra ít nhất hai điểm khác biệt chính về ontology, kiểu dữ liệu, hoặc xử lý thời gian. (Tham khảo `IE650_KG_06_Public-Knowledge-Graphs.pdf`)

---

## Câu 2: Mô hình hóa dữ liệu với RDF và Serialization (2.5 điểm)

Cho đoạn mô tả về một giải bóng đá và các cầu thủ:

> **Giải Ngoại hạng Anh (Premier League) mùa giải 2023-2024 có câu lạc bộ Arsenal. Arsenal có cầu thủ Martin Ødegaard (sinh ngày 1998-12-17, vị trí tiền vệ, số áo 8) và Bukayo Saka (sinh 2001-09-05, vị trí tiền đạo cánh, số áo 7). Huấn luyện viên của Arsenal là Mikel Arteta. Trong trận đấu ngày 2024-04-23, Arsenal gặp Chelsea tại sân nhà Emirates, kết quả hòa 2-2. Ødegaard ghi một bàn thắng ở phút 15.**

**Yêu cầu:**

**a)** Biểu diễn các thông tin trên thành bộ ba RDF. Sử dụng các URI tự định nghĩa hợp lý (gợi ý prefix: `league:`, `club:`, `player:`, `match:`, `coach:`, `xsd:`, `rdf:`).

**b)** Serialize dữ liệu dưới định dạng **Turtle** (đầy đủ prefix) và **N-Triples** (dòng đơn giản, mỗi triple một dòng, không prefix). N-Triples là dạng cơ bản nhất, mọi URI phải viết đầy đủ trong ngoặc `<>`, literal trong `""`.

**c)** Xác định trong đồ thị RDF của bạn có blank node hay không? Nếu có, giải thích mục đích sử dụng blank node. Nếu không, hãy sửa lại một phần dữ liệu để xuất hiện blank node (ví dụ mô tả “bàn thắng” như một sự kiện có thời gian và cầu thủ) và viết lại các triple tương ứng.

---

## Câu 3: Ngôn ngữ truy vấn SPARQL (2.0 điểm)

Xét knowledge graph về các công ty khởi nghiệp (startup) với lược đồ sau (dạng Turtle mẫu, không cần dùng file cụ thể):

```turtle
@prefix : <http://example.org/startup/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

:Startup rdf:type rdfs:Class .
:Founder rdf:type rdfs:Class .
:Investment rdf:type rdfs:Class .

:hasFounder rdf:type rdf:Property ; rdfs:domain :Startup ; rdfs:range :Founder .
:hasInvestment rdf:type rdf:Property ; rdfs:domain :Startup ; rdfs:range :Investment .
:amount rdf:type rdf:Property ; rdfs:domain :Investment ; rdfs:range xsd:decimal .
:year rdf:type rdf:Property ; rdfs:domain :Investment ; rdfs:range xsd:gYear .
:name rdf:type rdf:Property ; rdfs:range xsd:string .
```

Dữ liệu giả định có các startup: “TechA” (founder “Alice”, investment 1.5M USD năm 2021), “BioB” (founder “Bob”, investment 2.0M năm 2022, và một vòng khác 0.5M năm 2023), “GreenC” (founder “Carol”, chưa có investment).

**Yêu cầu:** Viết các truy vấn SPARQL:

**a)** Tìm tên các startup có tổng số tiền đầu tư (sum of all investments) lớn hơn 1.8M USD. Kết quả gồm tên startup và tổng tiền. Sử dụng GROUP BY và HAVING.

**b)** Tìm các founder (người sáng lập) có ít nhất hai startup khác nhau. Viết truy vấn SELECT trả về tên founder và danh sách các startup (dùng `GROUP_CONCAT` để gộp tên startup).

**c)** Viết truy vấn CONSTRUCT để tạo ra đồ thị mới chỉ gồm các cặp (founder, startup) mà startup có investment ít nhất một vòng. Sử dụng predicate mới `:founded`.

---

## Câu 4: Thiết kế Ontology và Logic mô tả (1.5 điểm)

**a)** Thiết kế ontology cho lĩnh vực **y tế bệnh viện** với các yêu cầu sau:
- Các lớp: `Patient`, `Doctor`, `Disease`, `Treatment`.
- Object property: `hasDiagnosis` (Patient → Disease), `prescribes` (Doctor → Treatment).
- Object property có tính transitive: `isLocatedIn` (dùng cho khoa/phòng, nhưng yêu cầu đơn giản: `isLocatedIn` có tính bắc cầu, ví dụ Phòng A nằm trong Khoa B, Khoa B nằm trong Bệnh viện C ⇒ Phòng A nằm trong Bệnh viện C).
- Data property: `hasDiseaseCode` (Disease → xsd:string, functional).
- Ràng buộc: Mỗi `Patient` phải có ít nhất một `hasDiagnosis`.

Hãy biểu diễn ontology bằng OWL/RDFS (cú pháp Turtle hoặc mô tả bằng lời kèm logic). Chỉ rõ các đặc tính (functional, transitive, v.v.).

**b)** Chuyển câu sau thành Description Logic (dùng ALC hoặc SHOIN):  
*“Mọi bệnh nhân được chẩn đoán mắc bệnh ‘COVID-19’ đều được chỉ định ít nhất một phương pháp điều trị bởi một bác sĩ chuyên khoa Nhi (Pediatrician).”*  
(Giả sử có các khái niệm: `Patient`, `Disease`, `Treatment`, `Pediatrician`; roles: `hasDiagnosis`, `prescribes`, `isSpecialistOf` (cho bác sĩ).)

**c)** Cho biết sự khác biệt giữa `owl:allValuesFrom` và `owl:someValuesFrom`. Lấy ví dụ cụ thể từ lĩnh vực thư viện (ví dụ: “sách tham khảo chỉ có tác giả là giáo sư” vs “sách có ít nhất một tác giả là giáo sư”).

---

## Câu 5: Suy luận và Thế giới mở (2.0 điểm)

**a)** Sử dụng bảng deduction rules của RDFS (trong tài liệu 03_RDFS trang 38), hãy suy diễn tất cả các triple mới từ tập triple sau:

```turtle
:Professor rdfs:subClassOf :Academic .
:Academic rdfs:subClassOf :Person .
:teachesCourse rdfs:domain :Professor .
:teachesCourse rdfs:range :Course .
:teachesCourse rdfs:subPropertyOf :involves .
:DrSmith rdf:type :Professor .
:DrSmith :teachesCourse :CS101 .
```

Liệt kê từng bước và chỉ rõ quy tắc áp dụng.

**b)** Cho ontology OWL sau:

```turtle
:Wine owl:disjointUnionOf ( :RedWine :WhiteWine :RoseWine ) .
:RedWine rdfs:subClassOf [ a owl:Restriction ; owl:onProperty :hasColor ; owl:hasValue "red" ] .
:WhiteWine rdfs:subClassOf [ a owl:Restriction ; owl:onProperty :hasColor ; owl:hasValue "white" ] .
:RoseWine rdfs:subClassOf [ a owl:Restriction ; owl:onProperty :hasColor ; owl:hasValue "rose" ] .
:MyWine a :RedWine .
:MyWine :hasColor "white" .
```

Hãy xác định ontology này có inconsistent không? Giải thích. Nếu thay `:MyWine a :RedWine` bằng `:MyWine rdf:type owl:Thing` thì có thay đổi gì? Nêu nguyên lý.

**c)** Thảo luận về “Non-unique Name Assumption” (NUNA) trong RDF và “Unique Name Assumption” (UNA) trong cơ sở dữ liệu. Dùng ví dụ về hai URI `:VB` và `:Vietcombank` để giải thích tại sao trong Semantic Web, nếu không có `owl:sameAs`, máy tính không thể kết luận chúng là một. Làm thế nào để khẳng định chúng khác nhau?

---

# ĐÁP ÁN – ĐỀ KG-03

## Câu 1: Kiến trúc và Nguyên lý

**a) Semantic Web Stack và các tầng trên**

Tài liệu: 02_RDF trang 7, 03_RDFS trang 4, 05_SPARQL trang 6, 09-OWL2 trang 3.

Các tầng từ dưới lên: Unicode/URI → XML → RDF → RDFS → OWL → SPARQL → Rules/Logic → Proof → Trust.

Tầng Logic, Proof, Trust ít được triển khai vì:
- Tính phân tán, khó đạt được sự đồng thuận về mặt logic và bằng chứng trên toàn web.
- Trust (tin cậy) yêu cầu xác thực nguồn, chữ ký số, và các cơ chế phức tạp, chưa được chuẩn hóa rộng.
- Hầu hết các ứng dụng thực tế dừng lại ở OWL/SPARQL là đủ để tích hợp và suy luận cơ bản.

**b) Content negotiation**

Tài liệu 02_RDF trang 37-41.

- **Cách 1: Link tới file RDF riêng** (ví dụ `<link rel="alternate" type="application/rdf+xml" href="data.rdf">` trong HTML). Ưu điểm: không cần cấu hình server phức tạp. Nhược điểm: “double bookkeeping” – thông tin hai nơi, dễ không đồng bộ.
- **Cách 2: Content negotiation** – client gửi HTTP header `Accept: application/rdf+xml`, server trả về RDF nếu được yêu cầu; nếu không, trả HTML. Ưu điểm: một URI cho cả người và máy. Nhược điểm: yêu cầu cấu hình server đặc biệt (Vary header, xử lý 303 redirects). Cả hai đều có nguy cơ không nhất quán.

**c) DBpedia vs YAGO**

Dựa trên `IE650_KG_06_Public-Knowledge-Graphs.pdf` (trang 24-27, 29):
- **DBpedia**: Sử dụng infobox extraction + mapping templates (người dùng định nghĩa ánh xạ từ template Wikipedia sang ontology). Có ontology (DBpedia ontology) với ~760 lớp (2020). Sử dụng category làm phân loại nhưng không chặt chẽ.
- **YAGO**: Sử dụng Wikipedia categories kết hợp với WordNet để tạo phân cấp lớp (hơn 500k loại). YAGO hỗ trợ yếu tố thời gian (time indexing) – mỗi sự kiện có thời gian bắt đầu/kết thúc (ví dụ cầu thủ chơi cho đội bóng trong một khoảng thời gian) dùng reification. DBpedia xử lý thời gian kém hơn.

---

## Câu 2: Mô hình hóa RDF

**a) Bộ ba RDF**

Prefixes:
```turtle
@prefix league: <http://example.org/league/> .
@prefix club: <http://example.org/club/> .
@prefix player: <http://example.org/player/> .
@prefix match: <http://example.org/match/> .
@prefix coach: <http://example.org/coach/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix : <http://example.org/ns/> .  (có thể dùng chung)
```

Các triple liệt kê (chọn lọc):

1. `league:PremierLeague rdf:type :League ; :season "2023-2024" .`
2. `club:Arsenal rdf:type :FootballClub ; :playsIn league:PremierLeague .`
3. `player:Odegaard rdf:type :Player ; :name "Martin Ødegaard"@en ; :birthDate "1998-12-17"^^xsd:date ; :position "Midfielder" ; :shirtNumber "8" ; :playsFor club:Arsenal .`
4. `player:Saka rdf:type :Player ; :name "Bukayo Saka"@en ; :birthDate "2001-09-05"^^xsd:date ; :position "Winger" ; :shirtNumber "7" ; :playsFor club:Arsenal .`
5. `coach:Arteta rdf:type :Coach ; :name "Mikel Arteta"@en ; :coaches club:Arsenal .`
6. `match:M240423 rdf:type :Match ; :homeTeam club:Arsenal ; :awayTeam club:Chelsea ; :date "2024-04-23"^^xsd:date ; :venue "Emirates Stadium" ; :result "2-2" .`
7. `match:M240423 :hasEvent [ a :Goal ; :scoredBy player:Odegaard ; :minute "15"^^xsd:integer ] .`

(Chú ý: Có thể model `hasEvent` với blank node).

**b) Serialization**

**Turtle** (đã thể hiện ở trên). **N-Triples** yêu cầu mỗi triple trên một dòng, không prefix, URI trong `<>`:

```nt
<http://example.org/league/PremierLeague> <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://example.org/ns/League> .
<http://example.org/league/PremierLeague> <http://example.org/ns/season> "2023-2024" .
<http://example.org/club/Arsenal> <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://example.org/ns/FootballClub> .
<http://example.org/player/Odegaard> <http://example.org/ns/name> "Martin Ødegaard"@en .
...
<http://example.org/match/M240423> <http://example.org/ns/hasEvent> _:b1 .
_:b1 <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://example.org/ns/Goal> .
_:b1 <http://example.org/ns/scoredBy> <http://example.org/player/Odegaard> .
_:b1 <http://example.org/ns/minute> "15"^^<http://www.w3.org/2001/XMLSchema#integer> .
```

**c) Blank node**

Trong mô hình trên, sự kiện bàn thắng (`:hasEvent [ a :Goal ; ... ]`) tạo ra **blank node** (không có URI). Blank node dùng để mô tả một thực thể vô danh, không cần định danh toàn cục, thường dùng cho n-ary relations (tài liệu 02_RDF trang 27-28). Nếu muốn tránh blank node, có thể tạo URI riêng cho mỗi sự kiện (ví dụ `match:M240423_goal1`).

---

## Câu 3: SPARQL

**a) Tổng tiền đầu tư > 1.8M**

```sparql
PREFIX : <http://example.org/startup/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT ?startupName (SUM(?amount) AS ?totalInvestment)
WHERE {
  ?startup :name ?startupName .
  ?startup :hasInvestment ?inv .
  ?inv :amount ?amount .
}
GROUP BY ?startup ?startupName
HAVING (SUM(?amount) > 1.8)
```

**b) Founder có ít nhất hai startup**

```sparql
PREFIX : <http://example.org/startup/>

SELECT ?founderName (GROUP_CONCAT(?startupName; SEPARATOR=", ") AS ?startups)
WHERE {
  ?startup :name ?startupName .
  ?startup :hasFounder ?founder .
  ?founder :name ?founderName .
}
GROUP BY ?founder ?founderName
HAVING (COUNT(?startup) >= 2)
```

**c) CONSTRUCT tạo `:founded`**

```sparql
PREFIX : <http://example.org/startup/>

CONSTRUCT {
  ?founder :founded ?startup .
}
WHERE {
  ?startup :hasInvestment ?inv .
  ?startup :hasFounder ?founder .
}
```

(Lưu ý: Truy vấn trên sẽ lặp lại nếu startup có nhiều investment, có thể dùng DISTINCT trong CONSTRUCT hoặc dùng subquery để lấy startup có investment rồi mới construct.)

---

## Câu 4: Thiết kế Ontology và Logic mô tả

**a) Ontology bệnh viện (Turtle)**

```turtle
@prefix : <http://example.org/hospital/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix owl: <http://www.w3.org/2002/07/owl#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

:Patient rdf:type owl:Class .
:Doctor rdf:type owl:Class .
:Disease rdf:type owl:Class .
:Treatment rdf:type owl:Class .

:hasDiagnosis rdf:type owl:ObjectProperty ; rdfs:domain :Patient ; rdfs:range :Disease .
:prescribes rdf:type owl:ObjectProperty ; rdfs:domain :Doctor ; rdfs:range :Treatment .
:isLocatedIn rdf:type owl:TransitiveProperty ; rdfs:domain :Place ; rdfs:range :Place .
:hasDiseaseCode rdf:type owl:DatatypeProperty , owl:FunctionalProperty ; rdfs:domain :Disease ; rdfs:range xsd:string .

:Patient rdfs:subClassOf [ a owl:Restriction ; owl:onProperty :hasDiagnosis ; owl:minCardinality "1"^^xsd:integer ] .
```

**b) Chuyển sang DL**

Câu: “Mọi bệnh nhân được chẩn đoán mắc bệnh ‘COVID-19’ đều được chỉ định ít nhất một phương pháp điều trị bởi một bác sĩ chuyên khoa Nhi.”

Ký hiệu:  
- `Patient` ≡ P, `Disease` ≡ D, `Treatment` ≡ T, `Pediatrician` ≡ Ped  
- `hasDiagnosis` ≡ diag, `prescribes` ≡ presc, `isSpecialistOf` ≡ spec (specialty)

Diễn đạt:  
`Patient ⊓ (∃ diag. ({COVID19})) ⊑ ∃ presc. (Treatment ⊓ ∃ spec⁻. (Ped))`  
Có thể đọc: Bệnh nhân có chẩn đoán là COVID-19 thì được chỉ định một treatment mà treatment có liên quan đến bác sĩ chuyên khoa Nhi qua quan hệ prescribes (ngược chiều). Chính xác hơn: `∃ presc. (Treatment ⊓ (∃ presc⁻. (Doctor ⊓ (∀ hasSpecialty. {Pediatric}))))` nhưng dài.

Trong khuôn khổ, chấp nhận:  
`P ⊓ ∃ diag.{COVID19} ⊑ ∃ presc. (T ⊓ ∃ (presc⁻) . (Doctor ⊓ ∃ hasSpecialty.{Pediatric}))`

**c) `allValuesFrom` vs `someValuesFrom`**

- `owl:allValuesFrom` : tất cả các giá trị của property phải thuộc về class đó (∀).  
  Ví dụ: “Sách tham khảo chỉ có tác giả là giáo sư” → `:ReferenceBook rdfs:subClassOf [ owl:onProperty :author ; owl:allValuesFrom :Professor ]`. Nếu một cuốn sách tham khảo có tác giả không phải giáo sư, reasoner sẽ phát hiện mâu thuẫn.
- `owl:someValuesFrom` : có ít nhất một giá trị thuộc class đó (∃).  
  Ví dụ: “Sách có ít nhất một tác giả là giáo sư” → `:Book rdfs:subClassOf [ owl:onProperty :author ; owl:someValuesFrom :Professor ]`.

Tài liệu 06_OWL trang 33.

---

## Câu 5: Suy luận và Thế giới mở

**a) Suy diễn RDFS**

Các triple gốc (viết tắt):
1. `:Professor rdfs:subClassOf :Academic` (a)
2. `:Academic rdfs:subClassOf :Person` (b)
3. `:teachesCourse rdfs:domain :Professor` (c)
4. `:teachesCourse rdfs:range :Course` (d)
5. `:teachesCourse rdfs:subPropertyOf :involves` (e)
6. `:DrSmith rdf:type :Professor` (f)
7. `:DrSmith :teachesCourse :CS101` (g)

Áp dụng:
- **rdfs9** từ (f) và (a): `:DrSmith rdf:type :Academic`.
- **rdfs9** từ `:DrSmith a :Academic` và (b): `:DrSmith rdf:type :Person`.
- **rdfs2** từ (g) và (c): `:DrSmith rdf:type :Professor` (đã có).
- **rdfs3** từ (g) và (d): `:CS101 rdf:type :Course`.
- **rdfs7** từ (e) và (g): `:DrSmith :involves :CS101`.

Kết quả: `:DrSmith a :Academic`, `:DrSmith a :Person`, `:CS101 a :Course`, `:DrSmith :involves :CS101`.

**b) Inconsistency**

`owl:disjointUnionOf` nghĩa là ba lớp `RedWine, WhiteWine, RoseWine` rời nhau (pairwise disjoint) và hợp của chúng bằng `:Wine`.  
`:MyWine a :RedWine` ⇒ `:MyWine :hasColor "red"` (từ restriction). Nhưng lại có `:MyWine :hasColor "white"`. Mâu thuẫn vì một cá thể không thể có hai giá trị khác nhau cho cùng property nếu property không được khai báo (nếu `:hasColor` là functional thì càng mâu thuẫn; nếu không functional thì vẫn có hai giá trị, nhưng restriction `hasValue "red"` bị vi phạm vì không phải mọi giá trị đều là red? `hasValue` yêu cầu object chính xác là literal đó – nếu thêm một giá trị khác, vẫn có giá trị `"red"`? Cần xét: `:RedWine rdfs:subClassOf [ hasValue "red" ]` nghĩa là mọi thể hiện của RedWine phải có triple `hasColor "red"`. Có triple đó và thêm `hasColor "white"` là không mâu thuẫn trực tiếp với subClassOf (vì subClassOf chỉ yêu cầu *có* giá trị "red", không cấm thêm). Nhưng với `disjointUnionOf`, `:MyWine` là RedWine nên không thể là WhiteWine hay RoseWine. Tuy nhiên có `hasColor "white"` không tự động suy ra nó là WhiteWine. **Kết luận**: Ontology này **consistent**? Thực tế, `hasValue` chỉ yêu cầu tồn tại triple đó. Hai triple cùng property là được. Không có axiom nào cấm điều đó. Vậy ontology vẫn consistent. Nhưng nếu thêm `:hasColor owl:FunctionalProperty` thì sẽ inconsistent. Tài liệu về `hasValue` (06_OWL trang 49) không nói về uniqueness.

Vì vậy đáp án: Ontology **không inconsistent** chỉ với thông tin đã cho. Nếu thay `:MyWine a :RedWine` thành `:MyWine rdf:type owl:Thing` thì không có ràng buộc `hasValue "red"`, do đó không mâu thuẫn.

(Sinh viên có thể tranh luận: Nếu dùng `owl:hasValue` như ràng buộc “giá trị bắt buộc”, việc có thêm giá trị khác không vi phạm, nhưng thường trong OWL, `hasValue` được hiểu là “có ít nhất một giá trị đó”, không loại trừ giá trị khác. Chấp nhận giải thích.)

**c) Non-unique Name Assumption (NUNA)**

- Trong RDF, giả định rằng hai URI khác nhau có thể trỏ đến cùng một thực thể (NUNA). Do đó, `:VB` và `:Vietcombank` có thể là cùng một ngân hàng, máy tính không tự biết.
- Trong cơ sở dữ liệu (UNA), mỗi tên (khóa chính) xác định duy nhất một bản ghi, nên hai tên khác nhau chắc chắn là hai thực thể khác nhau.
- Để khẳng định `:VB` và `:Vietcombank` là **cùng một** trong Semantic Web, dùng `:VB owl:sameAs :Vietcombank`.
- Để khẳng định chúng **khác nhau**, dùng `:VB owl:differentFrom :Vietcombank` (hoặc khai báo trong danh sách `owl:AllDifferent`). Tài liệu 06_OWL trang 14-16.



Dưới đây là bảng **tổng hợp định nghĩa, khái niệm, thuật ngữ cốt lõi** môn Knowledge Graphs, được trích lọc trực tiếp từ các bài giảng đã cung cấp. Dùng để ôn tập nhanh trước khi thi.

---

## 1. NỀN TẢNG & KIẾN TRÚC

| Thuật ngữ | Định nghĩa / Nội dung chính | Nguồn |
|-----------|----------------------------|-------|
| **URI / URL** | URI (Uniform Resource Identifier) dùng để định danh tài nguyên; URL là loại URI có thể tra cứu (dereferenceable) trên Web. | 01_Intro, p54-55 |
| **Unicode** | Bộ ký tự chuẩn hóa hỗ trợ hơn 144.000 ký tự các ngôn ngữ, biểu tượng, emoji. | 01_Intro, p31-33 |
| **XML** | eXtensible Markup Language – ngôn ngữ đánh dấu phổ dụng, chỉ cú pháp không ngữ nghĩa. | 01_Intro, p34-44 |
| **Semantic Web Stack** | Các tầng: Unicode/URI → XML → RDF → RDFS → OWL → SPARQL → Rules → Logic → Proof → Trust. | 02_RDF, p7; 03_RDFS, p4; 09-OWL2, p3 |
| **AAA Principle** | “Anyone can say Anything about Anything” – bất kỳ ai cũng có thể xuất bản bất kỳ triple nào. | 03_RDFS, p50 |

---

## 2. RDF (RESOURCE DESCRIPTION FRAMEWORK)

| Thuật ngữ | Định nghĩa | Nguồn |
|-----------|------------|-------|
| **RDF Triple** | Bộ ba (subject, predicate, object). Subject là URI hoặc blank node; predicate là URI; object có thể là URI, blank node, hoặc literal. | 02_RDF, p8 |
| **RDF Graph** | Tập hợp các triple (có hướng, có nhãn, có thể chứa chu trình). | 02_RDF, p3-6 |
| **Literal** | Giá trị nguyên tử (string, integer, date,…) chỉ xuất hiện ở vị trí object. Có thể có datatype (xsd:integer) hoặc language tag (@en). | 02_RDF, p11, 15 |
| **Blank Node** | Node vô danh, dùng cho n-ary predicate hoặc đối tượng không cần định danh toàn cầu. Ký hiệu `_:x` hoặc `[ ]`. | 02_RDF, p26-28 |
| **Reification** | Cho phép nói về một câu (triple) như một tài nguyên. Dùng để gắn meta-data (nguồn, thời gian, độ tin cậy) cho triple. | 02_RDF, p54-57 |
| **Named Graph** | Gán một URI cho một tập triple (cơ chế lưu trữ và truy xuất ngữ cảnh). | 07_KG_Labeled_Property_Graphs, p10-11 |
| **RDF\*** | Mở rộng RDF cho phép quoted triple (triple làm subject/object). Hỗ trợ annotation trên cạnh. | 07_KG_Labeled_Property_Graphs, p14-18 |

---

## 3. RDF SERIALIZATION (ĐỊNH DẠNG)

| Định dạng | Đặc điểm | Nguồn |
|-----------|----------|-------|
| **Turtle** | Dạng text thân thiện, dùng prefix, hỗ trợ `;` và `,`. | 02_RDF, p19 |
| **RDF/XML** | Chuẩn W3C, dùng XML, phù hợp với tool xử lý XML. | 02_RDF, p20-22 |
| **JSON-LD** | JSON-based, dùng `@context` mapping, chuẩn W3C 2020. | 02_RDF, p23 |
| **N-Triples** | Dạng dòng, mỗi triple một dòng, không prefix, URI đặt trong `<>`. | Đề KG-03 |

---

## 4. RDFS (RDF SCHEMA)

| Khái niệm | Định nghĩa / Cú pháp | Nguồn |
|-----------|----------------------|-------|
| **Class** | Tập hợp các instance. Khai báo: `:City a rdfs:Class`. | 03_RDFS, p21 |
| **subClassOf** | Quan hệ thừa kế giữa các class. `:EuropeanState rdfs:subClassOf :State`. | 03_RDFS, p21 |
| **Property** | Quan hệ giữa subject và object. Khai báo: `:capitalOf a rdf:Property`. | 03_RDFS, p23 |
| **subPropertyOf** | Quan hệ thừa kế giữa các property. `:capitalOf rdfs:subPropertyOf :locatedIn`. | 03_RDFS, p23 |
| **domain / range** | Giới hạn kiểu của subject (`domain`) và object (`range`) của property. | 03_RDFS, p24 |
| **rdfs:label** | Nhãn dùng cho người đọc, có thể có ngôn ngữ. | 03_RDFS, p26 |
| **rdfs:comment** | Chú thích mô tả. | 03_RDFS, p26 |
| **Deduction Rules** | Quy tắc suy diễn (rdfs2, rdfs3, rdfs7, rdfs9, rdfs10, rdfs11). | 03_RDFS, p38 |

---

## 5. OWL (WEB ONTOLOGY LANGUAGE)

| Khái niệm | Định nghĩa | Nguồn |
|-----------|------------|-------|
| **OWL Lite / DL / Full** | Ba biến thể với expressive power tăng dần. OWL DL dựa trên Description Logics, đảm bảo quyết định được. | 06_OWL, p7 |
| **OWL2 Profiles** | EL (nhanh trên lớp lớn), QL (truy vấn trên CSDL quan hệ), RL (giống rule). | 09-OWL2, p11-13 |
| **owl:Class** | Lớp trong OWL. | 06_OWL, p9 |
| **owl:Thing / owl:Nothing** | Lớp phổ quát (chứa mọi thứ) và lớp rỗng. | 06_OWL, p9 |
| **owl:ObjectProperty** | Property nối giữa hai URI (instance). | 06_OWL, p12 |
| **owl:DatatypeProperty** | Property nối từ URI đến literal. | 06_OWL, p12 |
| **owl:TransitiveProperty** | Tính bắc cầu: `hasAncestor`. | 06_OWL, p18 |
| **owl:SymmetricProperty** | Tính đối xứng: `sitsOppositeOf`. | 06_OWL, p18 |
| **owl:FunctionalProperty** | Mỗi subject có **nhiều nhất một** object. | 06_OWL, p24 |
| **owl:InverseFunctionalProperty** | Mỗi object xác định duy nhất subject (giống khóa chính). | 06_OWL, p25 |
| **owl:inverseOf** | Quan hệ nghịch đảo: `hasParent` và `isParentOf`. | 06_OWL, p18 |
| **owl:sameAs / differentFrom** | Khẳng định hai URI là cùng / khác thực thể. | 06_OWL, p14-16 |
| **owl:disjointWith** | Hai lớp không có phần tử chung. | 06_OWL, p42 |
| **owl:equivalentClass / Property** | Hai class / property tương đương. | 06_OWL, p15 |
| **owl:unionOf / intersectionOf / complementOf** | Phép hợp, giao, bù trên lớp. | 06_OWL, p10,42 |
| **owl:oneOf** (enumerated class) | Liệt kê các cá thể của lớp (closed class). | 06_OWL, p48 |
| **owl:Restriction** | Ràng buộc địa phương trên property: `allValuesFrom`, `someValuesFrom`, `minCardinality`, `maxCardinality`, `cardinality`. | 06_OWL, p30-33 |
| **owl:hasValue** | Ràng buộc một giá trị cụ thể. | 06_OWL, p49 |
| **owl:propertyChainAxiom** (OWL2) | Xây dựng property từ chuỗi property. | 09-OWL2, p9-10 |

---

## 6. SPARQL

| Khái niệm | Mô tả | Nguồn |
|-----------|-------|-------|
| **Graph Pattern Matching** | Tìm subgraph khớp với pattern chứa biến. | 05_SPARQL, p10 |
| **SELECT** | Trả về bảng các ràng buộc biến. | 05_SPARQL, p17 |
| **CONSTRUCT** | Trả về một đồ thị RDF mới. | 05_SPARQL, p38 |
| **ASK** | Trả về true/false nếu pattern tồn tại. | 05_SPARQL, p36 |
| **DESCRIBE** | Trả về “mô tả” một resource (cài đặt phụ thuộc). | 05_SPARQL, p37 |
| **FILTER** | Lọc kết quả theo điều kiện (số, chuỗi, regex, hàm). | 05_SPARQL, p23-27 |
| **OPTIONAL** | Pattern không bắt buộc; nếu không khớp, biến nhận unbound. | 05_SPARQL, p29 |
| **UNION** | Hợp hai kết quả. | 05_SPARQL, p28 |
| **MINUS / NOT EXISTS** | Loại bỏ các binding có pattern khớp. | Đề KG-03 |
| **GROUP BY + HAVING** | Nhóm theo biến, sau đó lọc nhóm (dùng hàm tổng hợp COUNT, SUM,…). | 05_SPARQL, p31; đề KG-02 |
| **SERVICE** | Truy vấn liên federated (gọi SPARQL endpoint khác). | 05_SPARQL, p39 |
| **Triple Pattern Fragments** | Giải pháp cân bằng giữa SPARQL endpoint (tốn server) và RDF dump (tốn client). | 05_SPARQL, p48-52 |

---

## 7. LIÊN KẾT DỮ LIỆU & OPEN DATA

| Thuật ngữ | Nội dung | Nguồn |
|-----------|----------|-------|
| **Linked Data principles** | 1) Dùng URI, 2) Dùng HTTP URI dereferenceable, 3) Cung cấp info chuẩn khi tra cứu, 4) Bao gồm link đến URI khác. | 04_LOD, p53-54 |
| **Five Star Scheme** | ★: open license; ★★: machine-readable; ★★★: non-proprietary format; ★★★★: W3C standards (RDF); ★★★★★: links to other datasets. | 04_LOD, p16,55 |
| **LOD Cloud** | Tập hợp các knowledge graph công khai được interlink (DBpedia, Wikidata, YAGO, v.v.) | 04_LOD, p18-20 |
| **Content Negotiation** | Dùng header Accept để server trả về định dạng phù hợp (HTML, RDF). | 02_RDF, p37-41 |
| **RDFa / Microdata / JSON-LD** | Các cách nhúng RDF vào HTML. Microdata dùng với schema.org, tạo blank node. | 02_RDF, p42-49 |
| **schema.org** | Tập vocabulary chuẩn cho dữ liệu có cấu trúc trên web (sản phẩm, địa điểm, sự kiện, người,…). | 04_LOD, p46-48 |

---

## 8. KNOWLEDGE GRAPH & ONTOLOGY ENGINEERING

| Khái niệm | Định nghĩa | Nguồn |
|-----------|------------|-------|
| **Knowledge Graph** | Mạng lưới các thực thể (entities) và quan hệ, có schema/ontology, hỗ trợ suy diễn. | 01_Intro, p8-10 |
| **Ontology** | “Explicit specification of a conceptualization” (Gruber). Mô tả formal, shared, partial. | 03_RDFS, p16-19 |
| **Methontology** | Phương pháp xây dựng ontology từ glossary → taxonomy → binary relations → concept dictionary. | 10_Knowledge_Modeling, p10-12 |
| **Competency Questions** | Câu hỏi bằng ngôn ngữ tự nhiên mà ontology phải trả lời được, dùng để kiểm tra. | 10_Knowledge_Modeling, p9 |
| **OntoClean** | Phương pháp phân tích ontology dựa trên Rigidity (tính cứng nhắc), Identity (tiêu chuẩn đồng nhất), Unity (tính thống nhất). | 10_Knowledge_Modeling, p14-36 |
| **Top‑Level Ontology** | Ontology độc lập miền, cung cấp nền tảng chung (DOLCE, SUMO, Cyc). | 10_Knowledge_Modeling, p52-80 |
| **Design Pattern / Anti‑Pattern** | Mẫu giải pháp lặp lại / các lỗi thường gặp khi mô hình hóa (rampant classism, exclusivity). | 10_Knowledge_Modeling, p37-50 |

---

## 9. CÁC GIẢ ĐỊNH QUAN TRỌNG

| Giả định | Ý nghĩa | Hệ quả | Nguồn |
|----------|---------|--------|-------|
| **Open World Assumption (OWA)** | Thiếu thông tin không có nghĩa là sai. Sự kiện không có trong KG có thể đúng (chưa được nhập). | Không thể suy luận phủ định từ vắng mặt. | 02_RDF, p32-33 |
| **Non‑unique Name Assumption (NUNA)** | Hai URI khác nhau có thể chỉ cùng một thực thể. | Cần `owl:sameAs` để khẳng định đồng nhất; `owl:differentFrom` để khẳng định khác. | 02_RDF, p30 |
| **Unique Name Assumption (UNA)** (CSDL) | Mỗi tên khác nhau chỉ một đối tượng khác nhau. | Mặc định trong DB quan hệ. | 05_Suy_diễn |

---

## 10. SUY LUẬN & REASONING

| Phương pháp | Mô tả | Nguồn |
|-------------|-------|-------|
| **Forward chaining (RDFS)** | Áp dụng rule (rdfs2,3,7,9,…) liên tục đến khi không sinh triple mới. | 03_RDFS, p37-38 |
| **Tableau algorithm (OWL DL)** | Xây dựng các partial tableau, kiểm tra mâu thuẫn, dùng blocking để đảm bảo dừng. | 09-OWL2, p43-64 |
| **Class consistency** | Một lớp có thể có instance hay không? | 09-OWL2, p31 |
| **Inconsistency** | Khi ontology chứa mâu thuẫn (vd: `:C disjointWith :D` và `x a C, x a D`). | 09-OWL2, p25-26, p44 |
| **Reductio ad absurdum** | Chứng minh `C ⊑ D` bằng cách giả sử instance thỏa C và not D, tìm mâu thuẫn. | 09-OWL2, p27-30 |

---

## 11. MỘT SỐ KNOWLEDGE GRAPH CÔNG KHAI

| KG | Đặc điểm | Nguồn |
|----|----------|-------|
| **DBpedia** | Trích xuất từ infobox Wikipedia, ontology ~760 lớp, mapping template. | 04_LOD; KG-06 |
| **YAGO** | Dùng Wikipedia categories + WordNet, hỗ trợ thời gian (time‑indexed). | KG-06, p29 |
| **Wikidata** | Cộng tác, lưu provenance, hỗ trợ nhiều ngôn ngữ, lớn nhất (~52M instances). | KG-06, p10-14,35 |
| **Freebase** | Cộng tác, Google mua lại, ngừng 2016, chuyển một phần sang Wikidata. | KG-06, p7-8 |
| **NELL** | Never‑Ending Language Learner – trích xuất tự động từ văn bản. | KG-06, p28-31 |
| **WebIsA LOD** | Hypernymy relations từ text crawl (Common Crawl), dùng Hearst patterns. | KG-06, p83-87 |
