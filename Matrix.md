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