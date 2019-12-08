Bab 1:  Pengenalan
===========================

Jaringan bergerak (*mobile*), yang memiliki sejarah selama 40 tahun 
berdampingan dengan Internet, telah mengalami perubahan yang signifikan.
Dua generasi awal mendukung suara dan teks, kemudian datang 3G yang
menentukan transisi ke akses jalur lebar (*broadband*) dan mendukung laju
data ratusan kilobit per detik. Saat ini, industri menggunakan 4G dengan
laju data megabit per detik, dan dengan dimulainya transisi ke 5G,
diharapkan terjadi 10 kali peningkatan.

Namun 5G lebih dari sekadar penambahan *bandwidth*. Seperti halnya 3G
yang menentukan transisi dari suara ke *broadband*, 5G menjanjikan 
transisi dari layanan akses tunggal (konektivitas *broadband*) ke
kumpulan layanan dan perangkat ujung (*edge*) yang bervariasi,
termasuk dukungan untuk antarmuka pemakai imersif (seperti AR/VR),
aplikasi *mission-critical* (contoh keamanan publik, kendaraan otonom),
dan *Internet-of-Things* (IoT). Kasus-kasus ini akan mencakup
berbagai macam hal dari perkakas rumahan, robot industri, sampai
mobil yang berjalan sendiri, jadi 5G tidak hanya mendukung manusia
untuk mengakses Internet dari ponsel saja, tetapi juga kumpulan
perangkat otonom yang saling bekerja bersama untuk tujuan tertentu.
Semuanya membutuhkan arsitektur yang berbeda.

Kebutuhan untuk arsitektur ini ambisius, dan dapat disarikan dalam
tiga tujuan utama:

- mendukung *Massive Internet-of-Things*, yang memungkinkan perangkat
  dengan energi sangat rendah (baterai berdaya tahan 10+ tahun), 
  kompleksitas sangat rendah (puluhan bit per detik), dan kepadatan
  sangat tinggi (1 juta simpul per kilometer persegi).

- mendukung *Mission-Critical Control*, yang memungkinkan ketersediaan
  sangat tinggi (lebih dari :math:`10^{-5}` per milidetik), latensi
  sangat rendah (sampai dengan 1 milidetik), dan mobilitas ekstrim
  (sampai dengan 100 km/jam).
  
- mendukung *Enhanced Mobile Broadband*, yang memungkinkan kapasitas
  ekstrim (10 Tbps per kilometer persegi) dan laju data ekstrim 
  (multi-Gbps puncak, 100+ Mbps konstan).
  
Target-target ini tidak dapat diperoleh dalam semalam, namun menjadi
capaian setiap generasi jaringan bergerak dalam ikhtiar satu dekade.

Jaringan 5G, yang sedang dalam proses evolusi, memerlukan spesifikasi
standar, beragam pilihan implementasi, dan daftar panjang sasaran yang
dituju. Untuk itu akan ada banyak interpretasi, karena itu pendekatan
kami ketika menjelaskan 5G berdasar pada prinsip saling mendukung.
Prinsip pertama adalah menerapkan sebuah "lensa sistem" dengan
penjelasan urutan putusan desain yang menghasilkan solusi daripada
kembali menuliskan daftar panjang singkatan sebagai sebuah
*fait accompli*. Prinsip kedua yaitu melakukan disagregasi secara
agresif sistem tersebut. Membangun sebuah jaringan akses 5G yang
disagregasif, menerapkan virtualisasi, dan *software-defined* adalah
arah industri saat ini yang sedang dikejar (karena tujuan teknis dan
bisnis yang bagus), namun dengan melepas jaringan 5G menjadi
komponen-komponen dasar merupakan cara terbaik untuk menjelaskan
bagaimana cara kerja 5G. Hal ini juga membantu menggambarkan bagaimana
5G dapat berubah di kemudian hari dengan menawarkan nilai lebih besar
lagi.

Dengan demikian, tidak ada definisi tunggal dan komprehensif untuk 5G,
seperti halnya Internet. Sistem ini kompleks dan berubah, dibatasi oleh
sekumpulan standar yang bertujuan untuk memberikan bermacam kebebasan
kepada semua pemangku kepentingan. Pada bab selanjutnya akan dapat
dilihat dengan lebih jelas dari konteks mana kita berbicara, *standard*
(yang setiap orang harus lakukan untuk saling bekerjasama), *tren* (arah
mana industri tertuju), atau *pilihan implementasi* (contoh untuk
membuat diskusi menjadi lebih konkrit). Dengan mengadopsi sebuah
perspektif sistem, kami berharap dapat menjelaskan 5G dan membantu pembaca
mengikuti sistem yang kaya potensi dan berkembang cepat ini.

1.1 Lanskap Standardisasi
-----------------------------

Sejak 3G, perancangan generasi jaringan bergerak sesuai dengan standar
yang ditentukan oleh 3GPP (*3rd Generation Partnership Project*). Bahkan
meskipun ada "3G" di namanya, 3GPP masih mendefinisikan standar untuk 4G
dan 5G, masing-masing sesuai dengan urutan rilis standar. Rilis 15
dianggap sebagai titik pemisah antara 4G dan 5G, untuk Rilis 16
diharapkan akan tersedia di akhir 2019. Terkait dengan istilah, 4G
mengikuti lintasan evolusi multirilis yang disebut dengan *Long Term
Evolution (LTE)*. 5G juga berada pada lintasan yang mirip, dengan
beberapa rilis di dalam rentang perkembangannya.

Walaupun 5G lebih ambisius daripada 4G, memahami 4G adalah langkah awal
untuk mempelajari 5G, karena beberapa aspek pada 5G dapat dijelaskan
dengan melihat penambahan fitur pada 4G. Pada bab-bab berikutnya, kami
akan sering mengenalkan arsitektur 4G untuk memberikan dasar pada
komponen 5G yang terkait.

Seperti Wi-Fi, jaringan seluler mengirimkan data lewat bandwidth
tertentu dalam spektrum radio. Namun, tidak serupa dengan Wi-Fi yang
diizinkan untuk menggunakan kanal baik 2.4 or 5 GHz (pita frekuensi
ini tidak membutuhkan izin), pemerintah telah melelang dan memberikan
lisensi eksklusif untuk penggunaan bermacam pita frekuensi kepada
pada penyedia layanan 5G, yang akan menawarkan layanan akses bergerak
pada para pelanggan.

There is also a shared-license band at 3.5-GHz, called *Citizens
Broadband Radio Service (CBRS)*, set aside in North America for cellular
use. Similar spectrum is being set aside in other countries. The CBRS band
allows three tiers of users to share the spectrum: first right of use
goes to the original owners of this spectrum, naval radars and satellite
ground stations; followed by priority users who receive this right over
10MHz bands for three years via regional auctions; and finally the rest
of the population, who can access and utilize a portion of this band as
long as they first check with a central database of registered users.
CBRS, along with standardization efforts to extend cellular networks to
operate in the unlicensed bands, open the door for private cellular
networks similar to Wi-Fi.

The specific frequency bands that are licensed for cellular networks
vary around the world, and are complicated by the fact that network
operators often simultaneously support both old/legacy technologies and
new/next-generation technologies, each of which occupies a different
frequency band. The high-level summary is that traditional cellular
technologies range from 700-MHz to 2400-MHz, with new mid-spectrum
allocations now happening at 6-GHz, and millimeter-wave (mmWave)
allocations opening above 24-GHz.

While the specific frequency band is not directly relevant to
understanding 5G from an architectural perspective, it does impact the
physical-layer components, which in turn has indirect ramifications on
the overall 5G system. We identify and explain these ramifications
in later chapters.

1.2 Access Networks
-------------------

The cellular network is part of the access network that implements the
Internet’s so-called *last mile*. Other access technologies include
*Passive Optical Networks (PON)*, colloquially known as
Fiber-to-the-Home. These access networks are provided by both big and
small network operators. Global network operators like AT&T run access
networks at thousands of aggregation points-of-presence across a
country like the US, along with a national backbone that interconnects
those sites. Small regional and municipal network operators might run
an access network with one or two points-of-presence, and then connect
to the rest of the Internet through some large operator’s backbone.

In either case, access networks are physically anchored at thousands of
aggregation points-of-presence within close proximity to end users,
each of which serves anywhere from 1,000 to 100,000 subscribers,
depending on population density. In practice, the physical deployment
of these “edge” locations vary from operator to operator, but one
possible scenario is to anchor both the cellular and wireline access
networks in Telco *Central Offices*.

Historically, the Central Office—officially known as the *PSTN
(Public Switched Telephone Network) Central Office*—anchored wired
access (both telephony and broadband), while the cellular network
evolved independently by deploying a parallel set of *Mobile Telephone
Switching Offices (MTSO)*. Each MTSO serves as a *mobile aggregation*
point for the set of cell towers in a given geographic area. For our
purposes, the important idea is that such aggregation points exist, and
it is reasonable to think of them as defining the edge of the
operator-managed access network. For simplicity, we sometimes use the
term “Central Office” as a synonym for both types of edge sites.

1.3 Edge Cloud
--------------

Because of their wide distribution and close proximity to end users,
Central Offices are also an ideal place to host the edge cloud. But this
begs the question: What exactly is the edge cloud?

In a nutshell, the cloud began as a collection of warehouse-sized
datacenters, each of which provided a cost-effective way to power, cool,
and operate a scalable number of servers. Over time, this shared
infrastructure lowered the barrier to deploying scalable Internet
services, but today, there is increasing pressure to offer
low-latency/high-bandwidth cloud applications that cannot be effectively
implemented in centralized datacenters. Augmented Reality (AR), Virtual
Reality (VR), Internet-of-Things (IoT), Autonomous Vehicles are all
examples of this kind of application. This has resulted in a trend to
move some functionality out of the datacenter and towards the edge of
the network, closer to end users.

Where this edge is *physically* located depends on who you ask. If you
ask a network operator that already owns and operates thousands of
Central Offices, then their Central Offices are an obvious answer.
Others might claim the edge is located at the 14,000 Starbucks across
the US, and still others might point to the tens-of-thousands of cell
towers spread across the globe.

Our approach is to be location agnostic, but it is worth pointing out
that the cloud’s migration to the edge coincides with a second trend,
which is that network operators are re-architecting the access network
to use the same commodity hardware and best practices in building
scalable software as the cloud providers. Such a design, which is
sometimes referred to as *CORD (Central Office Re-architected as a
Datacenter)*, supports both the access network and edge services
co-located on a shared cloud platform. This platform is then replicated
across hundreds or thousands of sites (including, but not limited to,
Central Offices). So while we shouldn’t limit ourselves to the Central
Office as the only answer to the question of where the edge cloud is
located, it is becoming a viable option.

.. note::

    To learn about the technical origins of CORD, which was first 
    applied to fiber-based access networks (PON), see `Central Office 
    Re-architected as a Datacenter, IEEE Communications, October 2016 
    <https://wiki.opencord.org/download/attachments/1278027/PETERSON_CORD.pdf>`__. 

    To understand the business case for CORD (and CORD-inspired
    technologies), see the A.D. Little report `Who Dares Wins!
    How Access Transformation Can Fast-Track Evolution of
    Operator Production Platforms, September 2019
    <https://www.adlittle.com/en/who-dares-wins>`__.

When we get into the details of how 5G can be implemented in practice,
we use CORD as our exemplar. For now, the important thing to understand
is that 5G is being implemented as software running on commodity
hardware, rather than embedded in the special-purpose proprietary
hardware used in past generations. This has a significant impact on how
we think about 5G (and how we describe 5G), which will increasingly
become yet another software-based component in the cloud, as opposed to
an isolated and specialized technology attached to the periphery of the
cloud.

Keep in mind that our use of CORD as an exemplar is not to imply that
the edge cloud is limited to Central Offices. CORD is a good exemplar
because it is designed to host both edge services and access
technologies like 5G on a common platform, where the Telco Central
Office is one possible location to deploy such a platform.

An important takeaway from this discussion is that to understand how 5G
is being implemented, it is helpful to have a working understanding of
how clouds are built. This includes the use of *commodity hardware*
(both servers and white-box switches), horizontally scalable
*microservices* (also referred to as *cloud native*), and
*Software-Defined Networks (SDN)*. It is also helpful to have an
appreciation for how cloud software is developed, tested, deployed and
operated, including practices like *DevOps* and *Continuous Integration
/ Continuous Deployment (CI/CD)*.

.. note::

   If you are unfamiliar with DevOps—or more generally, with the
   operational issues cloud providers face—we recommend you read `Site
   Reliability Engineering: How Google Runs Production Systems
   <https://landing.google.com/sre/books/>`__.

One final note about terminology. Anyone that has been paying
attention to the discussion surrounding 5G will have undoubtedly heard
about *Network Function Virtualization (NFV)*, which involves moving
functionality that was once embedded in hardware appliances into VMs
running on commodity servers. In our experience, NFV is a stepping
stone towards the fully disaggregated and cloud native solution we
describe, and so we do not dwell on it. In effect, you can think of
the NFV initiative as largely consistent with the approach taken in
this book, but making some different engineering choices when we get
down into the specifics of the implementation.

