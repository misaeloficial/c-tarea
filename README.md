#include <iostream>
using namespace std;

struct Nodo {
    int valor;
    Nodo* sig;
};

int main() {
    Nodo* inicio = NULL;
    Nodo* fin = NULL;
    char rpt;

    while (true) {
        cout << "Desea ingresar un numero? (S/N): ";
        cin >> rpt;

        if (rpt == 'S' || rpt == 's') {
            int num;
            cout << "Numero: ";
            cin >> num;

            Nodo* nuevo = new Nodo;
            nuevo->valor = num;
            nuevo->sig = NULL;

            if (inicio == NULL) {
                inicio = nuevo;
                fin = nuevo;
            } else {
                fin->sig = nuevo;
                fin = nuevo;
            }
        } else if (rpt == 'N' || rpt == 'n') {
            break;
        } else {
            cout << "Opcion no valida.\n";
        }
    }

    cout << "\nLista:\n";
    Nodo* actual = inicio;
    while (actual != NULL) {
        cout << "[" << actual->valor << "] ";
        actual = actual->sig;
        if (actual != NULL) cout << "-> ";
    }
    cout << "-> NULL" << endl;

    // Liberar memoria
    actual = inicio;
    while (actual != NULL) {
        Nodo* temp = actual;
        actual = actual->sig;
        delete temp;
    }

    return 0;
}
