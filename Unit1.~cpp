/*
	tytul:		      Galukas (remastered)
	opis:		      podstawowe funkcje niezbedne do stworzenia prostej gry typu
                              'space invaders' ;) - gracz steruje dzialem, eliminujacym
                              nadlatujace statki kosmiczne wroga.
	autorzy:	      Jakub Ga³ek
	data:		      20.12.2018
	testowane pod:	      Borland Builder 6
	czas realizacji:      grudzien - styczen
	cel zadania:	      poprawienie umiejetnosci programowania,
                              zapoznanie z roznorodnymi srodowiskami programowania,
                              zapoznanie z API OpenGL
	praktyczny cel:	      wersja finalna powinna posiadac nastepujace cechy:
                              ^ mozliwosc ruchu w pionie
                              ^ teksturowane obiekty (statek, pociski, przeciwnicy)
                              + wieksza liczbe przeciwnikow
                              + przeciwnicy aktywni (atakujacy)
                              ^ gra powinna sie toczyc nad jakims terenem!
                              ^ wyswietlanie wynikow (ilosc trafien) w postaci tekstu na ekranie
                              ^ stopniowe uszkadzanie statku (pasek wskazujacy ilosc obrazen)
                              ^ dodatkowym atutem bedzie: muzyka, efekty dzwiekowe
                              ^ poprawiony renderer
*/
//---------------------------------------------------------------------------

#include <vcl.h>
#pragma hdrstop

#include "Unit1.h"
//---------------------------------------------------------------------------
#pragma package(smart_init)
#pragma resource "*.dfm"
TForm1 *Form1;

int x=0;   int X=0;
int y=8;   int Y=0;

AnsiString zest="0";
int zestrzeleni=0;

int do_przegranej=12;

//WARUNEK KOLIZJI
bool kolizja(TImage * statek1, TImage * przeciwnik)
{
 if(statek1->Left >= przeciwnik->Left-statek1->Width &&
    statek1->Left <= przeciwnik->Left+przeciwnik->Width &&
    statek1->Top >= przeciwnik->Top-statek1->Height &&
    statek1->Top <= przeciwnik->Top+przeciwnik->Height)
    {
     return true;
    }
    else return false;


}
//---------------------------------------------------------------------------
__fastcall TForm1::TForm1(TComponent* Owner)
        : TForm(Owner)
{
}
//---------------------------------------------------------------------------

void __fastcall TForm1::Timer_ladowanieTimer(TObject *Sender)
{
//WYŒWIETLENIE EKRANU £ADOWANIA
     loading->Visible= true;
     loading->Visible= false;
}
//---------------------------------------------------------------------------
void __fastcall TForm1::FormCreate(TObject *Sender)
{

  Timer_ladowanie->Enabled=true;

//ZA£ADOWANIE TEKSTUR OBIEKTÓW Z PLIKÓW "/DATA"
loading->Picture->LoadFromFile("Data/loading.bmp");
tlo1->Picture->LoadFromFile("Data/kosmos1.bmp");
tlo2->Picture->LoadFromFile("Data/kosmos1.bmp");
statek1->Picture->LoadFromFile("Data/statek1.bmp");
przeciwnik1->Picture->LoadFromFile("Data/przeciwnik.bmp");
przeciwnik2->Picture->LoadFromFile("Data/przeciwnik.bmp");
przeciwnik3->Picture->LoadFromFile("Data/przeciwnik.bmp");
przeciwnik4->Picture->LoadFromFile("Data/przeciwnik.bmp");
zaloga1->Picture->LoadFromFile("Data/zaloga.bmp");
zaloga2->Picture->LoadFromFile("Data/zaloga.bmp");
zaloga3->Picture->LoadFromFile("Data/zaloga.bmp");
zycie1->Picture->LoadFromFile("Data/life.bmp");
zycie2->Picture->LoadFromFile("Data/life.bmp");
zycie3->Picture->LoadFromFile("Data/life.bmp");
zycie4->Picture->LoadFromFile("Data/life.bmp");
naboje->Picture->LoadFromFile("Data/naboje.bmp");

    soundtrack->FileName = "Data/battle_of_teth.wav";
    soundtrack->Open();
    soundtrack->Play();

//WYGENEROWANIE POZYCJI POCZ¥TKOWYCH PRZECIWNIKÓW

    randomize();

    if (kolizja(przeciwnik1,przeciwnik2) == false &&
        kolizja(przeciwnik1,przeciwnik3) == false &&
        kolizja(przeciwnik1,przeciwnik4) == false)
    {
    przeciwnik1->Top=-10;
    przeciwnik1->Left=0+random(856-0)+1;
    }

    if (kolizja(przeciwnik2,przeciwnik1) == false &&
        kolizja(przeciwnik2,przeciwnik3) == false &&
        kolizja(przeciwnik2,przeciwnik4) == false)
    {
    przeciwnik2->Top=-10;
    przeciwnik2->Left=0+random(856-0)+1;
    }

    if (kolizja(przeciwnik3,przeciwnik1) == false &&
        kolizja(przeciwnik3,przeciwnik2) == false &&
        kolizja(przeciwnik3,przeciwnik4) == false)
    {
    przeciwnik3->Top=-10;
    przeciwnik3->Left=0+random(856-0)+1;
    }

    if (kolizja(przeciwnik4,przeciwnik1) == false &&
        kolizja(przeciwnik4,przeciwnik2) == false &&
        kolizja(przeciwnik4,przeciwnik3) == false)
    {
    przeciwnik4->Top=-10;
    przeciwnik4->Left=0+random(856-0)+1;
    }

}
//---------------------------------------------------------------------------
void __fastcall TForm1::Timer_przeciwnikTimer(TObject *Sender)
{
if(loading->Visible== false)
{
//SPADANIE PRZECIWNIKÓW
 przeciwnik1->Left+=x;
 przeciwnik1->Top +=y;

 przeciwnik2->Left+=x;
 przeciwnik2->Top +=y;

 przeciwnik3->Left+=x;
 przeciwnik3->Top +=y;

 przeciwnik4->Left+=x;
 przeciwnik4->Top +=y;

//WYGENEROWANIE POZYCJI PRZECIWNIKÓW PO SPADNIÊCIU BEZKOLIZYJNYM
 if(przeciwnik1->Top>=730)
 {
    przeciwnik1->Top=-10;
    przeciwnik1->Left=0+random(856-0)+1;
 }
  if(przeciwnik2->Top>=730)
 {
    przeciwnik2->Top=-10;
    przeciwnik2->Left=0+random(856-0)+1;
 }
  if(przeciwnik3->Top>=730)
 {
    przeciwnik3->Top=-10;
    przeciwnik3->Left=0+random(856-0)+1;
 }
  if(przeciwnik4->Top>=730)
 {
    przeciwnik4->Top=-10;
    przeciwnik4->Left=0+random(856-0)+1;
 }

 //UTRATA ZA£OGI ORAZ SPADEK LICZBY ¯YÆ PODCZAS KOLIZJI

 if(do_przegranej <9) zaloga3->Visible=false;
 if(do_przegranej <5) zaloga2->Visible=false;
 if(do_przegranej <1) zaloga1->Visible=false;

 if(do_przegranej == 11)
 {
   zycie4->Visible=true;
   zycie3->Visible=true;
   zycie2->Visible=true;
   zycie1->Visible=false;
 }

  if(do_przegranej == 10)
 {
   zycie4->Visible=true;
   zycie3->Visible=true;
   zycie2->Visible=false;
   zycie1->Visible=false;
 }

  if(do_przegranej == 9)
 {
   zycie4->Visible=true;
   zycie3->Visible=false;
   zycie2->Visible=false;
   zycie1->Visible=false;
 }

  if(do_przegranej == 8)
 {
   zycie4->Visible=true;
   zycie3->Visible=true;
   zycie2->Visible=true;
   zycie1->Visible=true;
 }

  if(do_przegranej == 7)
 {
   zycie4->Visible=true;
   zycie3->Visible=true;
   zycie2->Visible=true;
   zycie1->Visible=false;
 }

  if(do_przegranej == 6)
 {
   zycie4->Visible=true;
   zycie3->Visible=true;
   zycie2->Visible=false;
   zycie1->Visible=false;
 }

  if(do_przegranej == 5)
 {
   zycie4->Visible=true;
   zycie3->Visible=false;
   zycie2->Visible=false;
   zycie1->Visible=false;
 }

  if(do_przegranej == 4)
 {
   zycie4->Visible=true;
   zycie3->Visible=true;
   zycie2->Visible=true;
   zycie1->Visible=true;
 }

  if(do_przegranej == 3)
 {
   zycie4->Visible=true;
   zycie3->Visible=true;
   zycie2->Visible=true;
   zycie1->Visible=false;
 }

  if(do_przegranej == 2)
 {
   zycie4->Visible=true;
   zycie3->Visible=true;
   zycie2->Visible=false;
   zycie1->Visible=false;
 }

  if(do_przegranej == 1)
 {
   zycie4->Visible=true;
   zycie3->Visible=false;
   zycie2->Visible=false;
   zycie1->Visible=false;
 }

 if(do_przegranej <= 0)
   {
    Timer_przeciwnik->Enabled=false;
    lewo->Enabled=false;
    prawo->Enabled=false;
    gora->Enabled=false;
    dol->Enabled=false;

    zycie4->Visible=false;
    ilosc_naboi->Visible=false;
    T_ilosc_naboi->Visible=false;
    przesuwanie->Enabled=false;
   // przeciwnik1->Visible=false;
   // przeciwnik2->Visible=false;
   // przeciwnik3->Visible=false;
   // przeciwnik4->Visible=false;


    if(Application->MessageBox(
    "Przegra³eœ!","Galukas",
    MB_OK | MB_ICONSTOP) == IDOK )
    {
       soundtrack->Close();
       Application->Terminate();
    }

   }

//POZYCJA (X,Y) WYSTRZA£U PO KOLIZJI Z PRZECIWNIKIEM
   if(naboje->Visible==false)
   {
     naboje->Left=statek1->Left;    //X
     naboje->Top=statek1->Top-100;  //Y
   }

//KOLIZJA Z PRZECIWNIKIEM
   //przeciwnik1
   if(kolizja(statek1,przeciwnik1) && przeciwnik1->Visible == true)
   {przeciwnik1->Visible=false; do_przegranej--;
   if(przeciwnik1->Visible==false)
   {
    przeciwnik1->Visible=true;
    przeciwnik1->Top=-10;
    przeciwnik1->Left=0+random(856-0)+1;
   }    }
   //przeciwnik2
   if(kolizja(statek1,przeciwnik2) && przeciwnik2->Visible == true)
   {przeciwnik2->Visible=false; do_przegranej--;
   if(przeciwnik2->Visible==false)
   {
    przeciwnik2->Visible=true;
    przeciwnik2->Top=-10;
    przeciwnik2->Left=0+random(856-0)+1;
   }    }
   //przeciwnik3
   if(kolizja(statek1,przeciwnik3) && przeciwnik3->Visible == true)
   {przeciwnik3->Visible=false; do_przegranej--;
   if(przeciwnik3->Visible==false)
   {
    przeciwnik3->Visible=true;
    przeciwnik3->Top=-10;
    przeciwnik3->Left=0+random(856-0)+1;
   }    }
   //przeciwnik4
   if(kolizja(statek1,przeciwnik4) && przeciwnik4->Visible == true)
   {przeciwnik4->Visible=false; do_przegranej--;
   if(przeciwnik4->Visible==false)
   {
    przeciwnik4->Visible=true;
    przeciwnik4->Top=-10;
    przeciwnik4->Left=0+random(856-0)+1;
   }     }

}
}
//---------------------------------------------------------------------------

void __fastcall TForm1::lewoTimer(TObject *Sender)
{
  if(loading->Visible==false)
  if(statek1->Left >0) statek1->Left -=10;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::prawoTimer(TObject *Sender)
{
  if(loading->Visible==false)
  if(statek1->Left+statek1->Width < tlo1->Width) statek1->Left +=10;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::goraTimer(TObject *Sender)
{
  if(loading->Visible==false)
  if(statek1->Top >0) statek1->Top -=10;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::dolTimer(TObject *Sender)
{
 if(loading->Visible==false)
 if(statek1->Top+statek1->Height < tlo1->Height) statek1->Top +=10;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::FormKeyDown(TObject *Sender, WORD &Key,
      TShiftState Shift)
{
    if (Key == VK_LEFT) lewo ->Enabled = true;
    if (Key == VK_RIGHT) prawo ->Enabled = true;
    if (Key == VK_UP) gora ->Enabled = true;
    if (Key == VK_DOWN) dol ->Enabled = true;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::FormKeyUp(TObject *Sender, WORD &Key,
      TShiftState Shift)
{
    if (Key == VK_LEFT) lewo ->Enabled = false;
    if (Key == VK_RIGHT) prawo ->Enabled = false;
    if (Key == VK_UP) gora ->Enabled = false;
    if (Key == VK_DOWN) dol ->Enabled = false;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::FormKeyPress(TObject *Sender, char &Key)
{

  if (Key == VK_SPACE)
  {
  if(ilosc_naboi->Caption=="1/1"&&
  loading->Visible==false)sndPlaySound("Data/strzal.wav",SND_ASYNC);
  Timer_naboje ->Enabled = true;
  ilosc_naboi->Caption="0/1";
  if(naboje->Top<=0)
  {
   //sndPlaySound("Data/strzal.wav",SND_ASYNC);

   //POZYCJA(X,Y)WYSTRZA£U
   naboje->Left=statek1->Left;    //X
   naboje->Top=statek1->Top-100;  //Y
  }

  }
//PAUZA GRY
 if (Key == VK_ESCAPE)
{
  system("pause");
}

}
//---------------------------------------------------------------------------

void __fastcall TForm1::Timer_nabojeTimer(TObject *Sender)
{
 //WYSTRZA£
 naboje->Visible = true;
 naboje->Left+=X;     //X
 naboje->Top -=y;     //Y
 if (naboje ->Top <=-100)
 ilosc_naboi->Caption="1/1";

 //ZESTRZLENIE PRZECIWNIKA
   //przeciwnik1
   if(kolizja(naboje,przeciwnik1) && przeciwnik1->Visible == true)
   {przeciwnik1->Visible=false; naboje->Visible=false;
   Timer_naboje ->Enabled = false;
   //ZLICZANIE ZESTRZELONYCH PRZECIWNIKÓW
   zestrzeleni++; zest = IntToStr(zestrzeleni);
   ilosc_zestrzelonych->Caption=zest;
   ilosc_naboi->Caption="1/1";

   if(przeciwnik1->Visible==false)
   {
    przeciwnik1->Visible=true;
    przeciwnik1->Top=-10;
    przeciwnik1->Left=0+random(856-0)+1;
   }    }
   //przeciwnik2
   if(kolizja(naboje,przeciwnik2) && przeciwnik2->Visible == true)
   {przeciwnik2->Visible=false; naboje->Visible=false;
   Timer_naboje ->Enabled = false;
   //ZLICZANIE ZESTRZELONYCH PRZECIWNIKÓW
   zestrzeleni++; zest = IntToStr(zestrzeleni);
   ilosc_zestrzelonych->Caption=zest;
   ilosc_naboi->Caption="1/1";

   if(przeciwnik2->Visible==false)
   {
    przeciwnik2->Visible=true;
    przeciwnik2->Top=-10;
    przeciwnik2->Left=0+random(856-0)+1;
   }    }
    //przeciwnik3
   if(kolizja(naboje,przeciwnik3) && przeciwnik3->Visible == true)
   {przeciwnik3->Visible=false; naboje->Visible=false;
   Timer_naboje ->Enabled = false;
   //ZLICZANIE ZESTRZELONYCH PRZECIWNIKÓW
   zestrzeleni++; zest = IntToStr(zestrzeleni);
   ilosc_zestrzelonych->Caption=zest;
   ilosc_naboi->Caption="1/1";

   if(przeciwnik3->Visible==false)
   {
    przeciwnik3->Visible=true;
    przeciwnik3->Top=-10;
    przeciwnik3->Left=0+random(856-0)+1;
   }    }
   //przeciwnik4
   if(kolizja(naboje,przeciwnik4) && przeciwnik4->Visible == true)
   {przeciwnik4->Visible=false; naboje->Visible=false;
   Timer_naboje ->Enabled = false;
   //ZLICZANIE ZESTRZELONYCH PRZECIWNIKÓW
   zestrzeleni++; zest = IntToStr(zestrzeleni);
   ilosc_zestrzelonych->Caption=zest;
   ilosc_naboi->Caption="1/1";

   if(przeciwnik4->Visible==false)
   {
    przeciwnik4->Visible=true;
    przeciwnik4->Top=-10;
    przeciwnik4->Left=0+random(856-0)+1;
   }    }


}
//---------------------------------------------------------------------------
void __fastcall TForm1::przesuwanieTimer(TObject *Sender)
{  if(loading->Visible==false)
{
   tlo1->Top -=1;
   if(tlo1->Top<1){tlo2->Top=0; tlo2->Top -=1; tlo1->Top =729;tlo1->Top -=1;}

   if(tlo2->Top<0){tlo2->Top -=1;}
}
}
//---------------------------------------------------------------------------



