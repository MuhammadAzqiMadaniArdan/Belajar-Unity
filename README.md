# Belajar-Unity
Sebuah Repository Pembelajaran Dasar Penggunaan Unity
<br>
<h5>❗ Catatan Dibawah merupakan rangkuman hasil pembelajaran yang saya pelajari jika ada kekurangan dalam isi materi atau salah mohon maaf dan dikoreksi ✍️ </h5>

<h1>0.Visibility </h1>

<img src="https://github.com/user-attachments/assets/3d815f9b-078e-4fae-8bc5-60878c4b1247"></img>

	Visibility adalah dasar object oriented Programming untuk melakukan visibilitas akses (public,private)

<h1>1.Void</h1>

<img src="https://github.com/user-attachments/assets/2330c5af-2d94-440e-a83f-90b79c15af4a"></img>


	void sama seperti menggunakan function tapi tidak membutuhkan return value dan dapat menggunakan visibility
	
	void start
	script atau isi code di dalam void start akan dijalankan sekali saat game baru dimulai

	void Update
	Script atau isi akan dipanggil terus menerus per frame rate atau fungsi yang akan terus terjadi selama game dalam kondisi jalan
	
	void FixedUpdate 
	sama seperti update tapi unity menyarankan penggunaan fixedUpdate daripada update untuk menggunakan atau mensinkronasikan component Rigidbody 
	atau hukum fisika (ex : gravitasi) 

	perbedaan antara update dan fixedupdate dapat dilihat jika keduanya menggunakan Debug.log("Waktu update" + Time.deltaTime)

	penggunaan fixedupdate memiliki Waktu yang sesuai dengan interaksi fisik seperti saat kita melakukan movement terhadap objek terkait 
	hasil : DebugLog (0.22) -> sinkron dan tidak berubah 

	sementara update memiliki Waktu sesuai per frame rate animasi / melakukan render secara terus menerus
	hasil : DebugLog (0.01,0.02,0.03) -> sinkron tetapi terus berubah setiap detiknya

<h1>1.25 Debug.log()</h1>

	Debug.log() sama seperti console.log() untuk melihat hasil dari code di console secara sistematis sebelum dieksekusi dalam program langsung

	contoh :
	
	Debug.log("Waktu update" + Time.deltaTime)

	keterangan : 
	
	perintah log : Debug.log
	Value : "Waktu update " + Time.deltaTime
	
	contoh hasil : Waktu update 0.22

	Jika ingin melakukan penggabungan console antara tipe data string dan integer menggunakan operator pertambahan / +

<h1>1.5 Variabel</h1>

<img src="https://github.com/user-attachments/assets/c606f480-1b1a-41ce-8953-f97247a17cf7"></img>

	> Variabel unity atau csharp sama pada penggunaan variable pada umumnya 

	contoh : 

		float horizontal = 3;
		float vertical = Input.GetAxis("Vertical");

	Keterangan :

	tipe data = float
	nama variable = horizontal dan vertical
	Value = 3 dan Input.GetAxis("Vertical")

	> Variabel bisa menggunakan visibity seperti dibawah ini:

	visibility / visibilitas (public,private)

	contoh variable diluar void  :

		public float kecepatan;

	keterangan :

	visibility : public
	tipe data : float
	nama variable : kecepatan

	contoh diatas adalah variable yang tidak memiliki value karena tidak ada isinya 
	maka harus melakukan pengisisan value manual di aplikasi unity

	> Tipe Data

	-> boolean : true / false

	dalam void jika kita mengambil variabel tipe boolean dapat dikelola secara langsung mana yang true atau false
	
	contoh : 

	bool IsDirt;

	jika menggunakan tanda seru !isDirt = hasilnya adalah false
	jika tidak maka isDirt   = true

	-> Transform

	-> Layermask

<h1>2.Vector</h1>

	Vector3 dan vector yang lain sama seperti penggunaan inisial variable seperti let,const atau var

	Vector 3 berisi movement seperti 3 isi yaitu x,y,z untuk melakukan pergerakan pada object yang kita mau
	Vector 2 berisi 2 movement yaitu x,y biasanya untuk rigidBody 
	(Semakin kecil angka dibelakang vector maka semakin sedikit value / parameter yang dibutuhkan )

	contoh pendeklarasian

		void update(){

			Vector3 jalan = new Vector3(Input.GetAxis("Horizontal"),0,0);

		}

	keterangan :

	Vector variabel = Vector3 jalan
	deklarasi isi = new Vector3()
	parameter / value = (Input.GetAxis("Horizontal"),0,0)
	x = Input.GetAxis("Horizontal")
	y = 0
	z = 0

<h1>3.Input</h1>

<img src="https://github.com/user-attachments/assets/2fc6ee8c-f274-40b9-b41b-2cbcb7c36e43"> </img>

	Unity memiliki input yang sudah disediakan agar kita bisa memakainya

	Bisa dilihat di unity->edit->project settings->Input manager

	contoh penggunaan :

		Vector3 jalan = new Vector3(Input.GetAxis("Horizontal"),0,0);


	keterangan :

	Input dari Unity = Input.GetAxis("Horizontal") -> menjalankan perintah gerakan secara horizontal

<h1>4.Animasi</h1>

	>Transform

	karena ingin merubah posisi objek bisa menggunakan = 

	transform.position += parameternya

	contoh :

		transform.position += jalan * Time.deltatime + kecepatan;

	keterangan:

	transform : transform.position
	parameter animasi : jalan * Time.deltatime + kecepatan
	Waktu : Time.deltatime
 

<h1>5.Hierarchy</h1>

Membuat sprite Kotak 2d = klik kanan di hierarcy + 2d Object + sprites + Square

Membuat script dari unity : 

Di bagian inspector punya sprite yang sudah dibuat sebelumnya (square), Add component,new script,nama script + enter

<h1>6.Component</h1>

>Menggunakan isi Component pada Codingan atau script

Harus melakukan Deklarasi di bagian class script agar dapat digunakan pada codingan

diluar void deklarasikan component yang ingin digunakan

didalam void start ambil data yang sudah dideklarasikan / variable deklarasi agar data component dapat dipakai selama game berjalan atau pada void update

contoh :

diluar void :

Rigidbody2D rb;

didalam void start :

void Start()
{

	rb = GetComponent<RigidBody2D>();

}

Keterangan :

Deklarasi Componet : Rigidbody2D rb;
variable deklarasi : rb =
Pengambilan Component / value = GetComponent<RigidBody2D>();


>RigidBody

Menambahkan Component RigidBody = Gravitasi pada objek

Jika Box atau sprite mengelilingi layer tanah maka berikan setting pada sprite rigid body 
constrain->freze->centang freeze z

>Box Collider 

Menambahkan Box Collider = dapat melakukan interaksi antara player dengan objek tersebut

(kedua sprite harus punya boxcollider)

contoh : 

player menyentuh tanah : player dan tanah harus punya component box collider

<h1>7.GetAxis</h1>

>GetAxis

melakukan step yang diinginkan atau pergerakan secara berkala dari -0.01 sampai kecepatan yang diinginkan

contoh :

kita memiliki variabel gerak untuk melakukan pergerakan player
Dengan gerak value = 5 
maka jika menggunakan rigidBody dapat dilihat di inspector 
pada bagian rigidBody->velocity->info akan menampilkan kecepatan velocity dari -0.01 sampai -0.05

Ketika berhenti terdapat efek mengerem seperti pada game mario bros (Lebih smooth)

>GetAxisRaw

melakukan step atau pergerakan yang diinginkan dengan ketetapan Waktu yang sudah dipersiapkan / tetap

contoh :

kita memiliki variabel gerak untuk melakukan pergerakan player
Dengan gerak value = 5 
maka jika menggunakan rigidBody dapat dilihat di inspector 
pada bagian rigidBody->velocity->info akan menampilkan kecepatan velocity langsung tetap menjadi -5 tanpa melakukannya secara berkala seperti GetAxis

 
<h1>8.Physic2D</h1>

->OverlapCircle()
 
	digunakan untuk mendeteksi apakah terdapat objek dalam radius lingkaran objek yang kita punya terhadap radius 
	tertentu pada posisi yang ditentukan



<h1>9.Physic Material 2d</h1>

create->2d->physic Material 2d

Berfungsi agar objek yang kita gunakan tidak menempel di objek yang memiliki box collider atau dinding samping

caranya setelah di create set friction 0
drag Physic Material 2d ke rigidbody objek -> material
