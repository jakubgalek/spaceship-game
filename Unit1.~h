//---------------------------------------------------------------------------

#ifndef Unit1H
#define Unit1H
//---------------------------------------------------------------------------
#include <Classes.hpp>
#include <Controls.hpp>
#include <StdCtrls.hpp>
#include <Forms.hpp>
#include <ExtCtrls.hpp>
#include <MPlayer.hpp>
#include <Graphics.hpp>
//---------------------------------------------------------------------------
class TForm1 : public TForm
{
__published:	// IDE-managed Components
        TImage *tlo1;
        TImage *statek1;
        TTimer *Timer_przeciwnik;
        TImage *przeciwnik1;
        TTimer *lewo;
        TTimer *prawo;
        TTimer *gora;
        TTimer *dol;
        TImage *zycie4;
        TImage *zycie3;
        TImage *zycie2;
        TImage *zycie1;
        TMediaPlayer *soundtrack;
        TImage *zaloga1;
        TImage *zaloga2;
        TImage *zaloga3;
        TImage *przeciwnik2;
        TImage *przeciwnik3;
        TImage *przeciwnik4;
        TImage *naboje;
        TTimer *Timer_naboje;
        TLabel *ilosc_naboi;
        TLabel *ilosc_zestrzelonych;
        TImage *loading;
        TTimer *Timer_ladowanie;
        TImage *T_ilosc_naboi;
        TImage *T_zestrzeleni_wrogowie;
        TTimer *przesuwanie;
        TImage *tlo2;
        void __fastcall FormCreate(TObject *Sender);
        void __fastcall Timer_przeciwnikTimer(TObject *Sender);
        void __fastcall lewoTimer(TObject *Sender);
        void __fastcall prawoTimer(TObject *Sender);
        void __fastcall goraTimer(TObject *Sender);
        void __fastcall dolTimer(TObject *Sender);
        void __fastcall FormKeyDown(TObject *Sender, WORD &Key,
          TShiftState Shift);
        void __fastcall FormKeyUp(TObject *Sender, WORD &Key,
          TShiftState Shift);
        void __fastcall FormKeyPress(TObject *Sender, char &Key);
        void __fastcall Timer_nabojeTimer(TObject *Sender);
        void __fastcall Timer_ladowanieTimer(TObject *Sender);
        void __fastcall przesuwanieTimer(TObject *Sender);
private:	// User declarations
public:		// User declarations
        __fastcall TForm1(TComponent* Owner);
};
//---------------------------------------------------------------------------
extern PACKAGE TForm1 *Form1;
//---------------------------------------------------------------------------
#endif
