# javaMap

package javaMap.base;

import java.util.ArrayList;


public class Kisi {
	int numara=0;
	String adı="";
	
	Kisi(int numara,String adı){setNumara(numara);setAdı(adı);}

	public int getNumara() {
		return numara;
	}

	public void setNumara(int numara) {
		this.numara = numara;
	}

	public String getAdı() {
		return adı;
	}

	public void setAdı(String adı) {
		this.adı = adı;
	}



}
package javaMap.base;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Runner {
	static Scanner sc = new Scanner(System.in);
	static String girilen;
	static int numara, sayac = 0;
	static List<Object> rehber = new ArrayList<>();
	//static List<String> rehber = new ArrayList<>();

	public static void main(String[] args) {

		while (girilen != "") {
			
			System.out.print("isim giriniz veya arama yapmak için a ya basınız");
			getir().toUpperCase();
			
			if (!girilen.equals("a")) {
				
				System.out.print("numara giriniz");
				
				if (numarakontrol(numaragetir())) {
					System.out.println("hatalı giriş");
				} else {
					Kisi p = new Kisi(numara, girilen);
					//rehber.add(p.getAdı() + "=" + p.getNumara());
					rehber.add(p);
					System.out.println("kayıt eklendi");
				}

			} else if (girilen.equals("a")) {
				
				System.out.print("arama yapmak istediğiniz ismi giriniz");
				getir().toUpperCase();
				
				for (int i = 0; i < rehber.size(); i++) {
					if (((Kisi) rehber.get(i)).getAdı().contains(girilen)) {
						sayac++;
						//System.out.println(rehber.get(i));
						System.out.println(((Kisi) rehber.get(i)).getAdı()+" tel no: "+((Kisi) rehber.get(i)).getNumara());
					}
				}
				if (sayac == 0) {
					System.out.println("kayıt bulunamadı");
				} else {
					System.out.println(sayac + " kayıt bulundu");
				}
				sayac = 0;
			}
		}
	}

	public static String getir() {
		girilen = sc.next();
		return girilen;
	}

	public static int numaragetir() {
		numara = sc.nextInt();
		return numara;
	}

	public static boolean numarakontrol(int numara) {
		boolean durum = false;
		if (!(numara + "").matches("[0-9]+") || (numara + "").length() != 8) {
			durum = true;
		}
		return durum;
	}
}
