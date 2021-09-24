# c-
//check this code, i am student of programming
#include <iostream>
using namespace std;
#include<string>
#include <typeinfo>
#include <string.h>
#include <stdlib.h>

string linha('-',69);
class Base{
    private:
        string titulo;
        string autor;
       public:
       Base *Proximo;
            virtual void set(){
                cout<<"entre com titlo: ";
                    cin>>titulo;
                 cout<<"entre com nome do autor: "  ;
                    cin>>autor;
            }
            virtual void show()=0;

            string get_t(){
                return titulo;
                }
              string get_a(){  
                return autor;
              }              
};
class Acao: public Base{
    string palavra_chave;
    string protagonista;

    public:
        void set(){
            system("cls");
            cout<<"======================= Cadastrar =============================="<<endl;
            Base::set();
            cout<<"entre com a palavra chave do livro: ";
                cin>>palavra_chave;
            cout<<"entre com o nome do protagonista: "    ;
                cin>>protagonista;  
        }
        void show(){
            system("cls");
            cout<<"=================================================="<<endl;
                cout<<"autor: "<<get_a()<<endl;
                cout<<"titulo: "<<get_t()<<endl;
                cout<<"palavra chave: "<<palavra_chave<<endl;
                cout<<"protagonista: "<<protagonista<<endl;
            cout<<"=================================================="<<endl;
        }

};
class Romance: public Base{
    string prologo;
    string par_romantico;

    public:
        void set(){
            cout<<"===================== Cadastrar ============================="<<endl;
            Base::set();
            cout<<"entre com o prologo: ";
                cin>>prologo;
             cout<<"entre com nome do par romantico: "   ;
                cin>>par_romantico;
        }
        void show(){
            cout<<"=================================================="<<endl;
              cout<<"autor: "<<get_a()<<endl;
                cout<<"titulo: "<<get_t()<<endl;
                cout<<"prologo: "<<prologo<<endl;
                cout<<"par_romantico: "<<par_romantico<<endl;
            cout<<"=================================================="<<endl;    
        }

};
bool teste(Base *obj){

    Acao *temp;

    if(temp= dynamic_cast<Acao*>(obj))
        return 1;
    else
        return 0;    

}
int main(){
    int i=0,opt,op;
    char choise;
    Base *obj[10];

        do{
            system("cls");
            cout<<linha<<endl<<"\t1-cadastrar"<<endl<<"\t2-visualizar"<<endl<<"\t3-apagar"<<endl<<"\t4-sair"<<endl<<linha<<endl;
                cin>>opt;
            switch(opt)    {
                case 1:
                    cout<<"cadastrar livor accao(1) ou Romance(2)"<<endl;
                        cin>>op;
                       if(op==1) 
                        obj[i]=new Acao();
                        else
                        obj[i]=new Romance();

                    obj[i++]->set();
                    system("pause>0");
                    break;
                case 2:    
                for(int j=0;j<i;j++){
                    if(teste(obj[j]))
                    obj[j]->show();
                    else
                    obj[j]->show();
                }
                system("pause");
                break;
                case 3:
                system("cls");
                cout<<"=============================== apagar ========================="<<endl;
                    cout<<"entre com a posicao a apagar: ";
                        cin>>op;
                       obj[op]->show();
                       cout<<"pretende apagar(y/): ";
                            cin>>choise;
                        if(choise=='y')    {
                            delete obj[op];
                            cout<<"apagado!!"<<endl;
                        }
                         else 
                         cout<<"cancelado!!"<<endl;
                         system("pause");
                         break;
            }

            

        }while(opt!=4);

    system("pause");
    return 0;
}
