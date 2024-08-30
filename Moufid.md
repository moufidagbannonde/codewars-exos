# Exercice1


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

# Exercice 2
## Rapport
 Le but de l'exercice est d'implémenter une matrice classe générique qui peut contenir une quantité fixe d'objets de tous types.

## Code
````java
public class Matrix<E> {
  private E[][] matrix; // Tableau 2D de type générique E

  public static void main(String[] args) {
    // point d'entrée du programme
  }



  public Matrix(int rows, int cols) {
      matrix = (E[][]) new Object[rows][cols]; // Initialise la matrice avec le nombre de lignes et colonnes spécifié
  }

  /*
   * Retourne l'élément à la position (i, j)
   */
  public E get(int i, int j) {
      return matrix[i-1][j-1]; // Retourne l'élément à la position (i, j) (indices basés sur 1)
  }

  /*
   * Définit l'élément à la position (i, j) avec la valeur donnée
   */
  public void set(int i, int j, E value) {
      matrix[i-1][j-1] = value; // Définit l'élément à la position (i, j) avec la valeur donnée
  }

  /*
   * Définit la ligne i avec les valeurs spécifiées
   * @param i la ligne à définir
   * @param values les valeurs à définir pour la ligne
   */
  public void setRow(int i, E... values) {
      matrix[i-1] = values; // Définit la ligne i avec les valeurs spécifiées
  }

  /*
   * Échange les éléments aux positions (i1, j1) et (i2, j2)
   */
  public void swap(int i1, int j1, int i2, int j2) {
      E temp = matrix[i1-1][j1-1]; // Stocke l'élément à la position (i1, j1) dans une variable temporaire
      matrix[i1-1][j1-1] = matrix[i2-1][j2-1]; // Remplace l'élément à la position (i1, j1) par celui à (i2, j2)
      matrix[i2-1][j2-1] = temp; // Remplace l'élément à la position (i2, j2) par la valeur temporaire
  }

  /*
   * Retourne une représentation en tableau 2D de chaînes de caractères de la matrice
   * @return un tableau 2D de chaînes de caractères représentant la matrice
   */
  public String[][] toArray() {
      String[][] arr = new String[matrix.length][matrix[0].length]; // Initialise un tableau 2D de chaînes de caractères avec les mêmes dimensions que la matrice
      for (int i = 0; i < matrix.length; i++) { // Pour chaque ligne de la matrice
          for (int j = 0; j < matrix[0].length; j++) { // Pour chaque colonne de la ligne
              arr[i][j] = String.valueOf(matrix[i][j]); // Convertit l'élément à la position (i, j) en chaîne de caractères et le stocke dans le tableau 2D
          }
      }
      return arr; // Retourne le tableau 2D de chaînes de caractères
  }
}

`````