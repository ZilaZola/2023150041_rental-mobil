# 2023150041_rental-mobil
// Abstract Class Kendaraan
abstract class Kendaraan {
    String nomorPolisi;
    String merk;

    Kendaraan(String nomorPolisi, String merk) {
        this.nomorPolisi = nomorPolisi;
        this.merk = merk;
    }

    abstract void infoKendaraan();
}

// Class Mobil turunan dari Kendaraan
class Mobil extends Kendaraan {
    Mobil(String nomorPolisi, String merk) {
        super(nomorPolisi, merk);
    }

    @Override
    void infoKendaraan() {
        System.out.println("Mobil: " + merk + " | Plat: " + nomorPolisi);
    }
}

// Interface Person
interface Person {
    String getNama();
}

// Class Supir implementasi dari Person
class Supir implements Person {
    String NIP;
    String nama;

    Supir(String NIP, String nama) {
        this.NIP = NIP;
        this.nama = nama;
    }

    public String getNama() {
        return nama;
    }
}

// Class Rental
class Rental {
    Mobil mobil;
    Supir supir;
    boolean sedangDipinjam;

    Rental(Mobil mobil, Supir supir) {
        this.mobil = mobil;
        this.supir = supir;
        this.sedangDipinjam = false;
    }

    void dipinjam() {
        if (!sedangDipinjam) {
            sedangDipinjam = true;
            System.out.println("Mobil " + mobil.merk + " dipinjam oleh " + supir.getNama());
        } else {
            System.out.println("Mobil sedang dipinjam!");
        }
    }

    void dikembalikan() {
        if (sedangDipinjam) {
            sedangDipinjam = false;
            System.out.println("Mobil " + mobil.merk + " telah dikembalikan oleh " + supir.getNama());
        } else {
            System.out.println("Mobil belum dipinjam.");
        }
    }
}

// Class Utama
public class Main {
    public static void main(String[] args) {
        Mobil m1 = new Mobil("B 1234 AB", "Toyota Avanza");
        Supir s1 = new Supir("198712", "Pak Budi");

        Rental rental1 = new Rental(m1, s1);

        m1.infoKendaraan();
        rental1.dipinjam();
        rental1.dikembalikan();
    }
}
