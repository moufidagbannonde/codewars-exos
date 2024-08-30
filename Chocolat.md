## Rapport
Le but de l'exercice était d'écrire une méthode qui, pour un ordre donné de portraits de deux barres de chocolat, détermine un nombre minimum de cassures que l'on devrait effectuer sur une première barre pour former une deuxième barre en repositionnant les parties cassées.

## Code
````java
public class Solution {

    public static int chocolate(int N, int firstBar[], int secondBar[]) {
        int result = N - 1; // Initialise le nombre de cassures potentielles à N - 1 (pire scénario où chaque case nécessite une cassure)
        int a[] = new int[N + 1]; // Crée un tableau 'a' de taille N + 1 pour stocker les relations d'ordre entre les confiseurs de 'firstBar'

        // Remplissage du tableau a avec les successeurs directs des confiseurs dans 'firstBar'
        for (int i = 1; i < N; i++) {
            a[firstBar[i - 1]] = firstBar[i];
            // Par exemple, si firstBar = {4, 3, 2, 5, 1}, alors après cette boucle,
            // a[4] = 3, a[3] = 2, a[2] = 5, a[5] = 1.
        }

        // Parcourt 'secondBar' pour vérifier les segments continus
        for (int i = 1; i < N; i++) {
            // Vérifie si l'élément suivant dans 'secondBar' suit l'ordre défini dans 'firstBar'
            if (a[secondBar[i - 1]] == secondBar[i]) {
                result--; // Si oui, on peut éviter une cassure donc on décrémente le résultat
            }
            // Par exemple, pour secondBar = {1, 2, 5, 3, 4}:
            // - a[1] == 2 est vrai, donc on décrémente result à N - 2,
            // - a[2] == 5 est vrai, donc on décrémente result à N - 3,
            // - a[5] == 3 est vrai, donc on décrémente result à N - 4,
            // - a[3] == 4 est vrai, donc on décrémente result à N - 5.
        }

        return result; // Retourne le nombre minimum de cassures nécessaires pour réorganiser firstBar en secondBar
    }
}

````