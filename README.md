# calculadora-de-matrices
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace calculadora_de_matrices
{
    public partial class Form1 : Form
    {
        private TextBox[,] matriz1;
        private TextBox[,] matriz2;
        private TextBox[,] resultante;
        private float determinante;
        int linea1, columna1;
        int linea2, columna2;
        private float CalculosMatrices;
       
    

        public Form1()
        {
            InitializeComponent();
        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void label4_Click(object sender, EventArgs e)
        {

        }

        private void crearmatriz2_Click(object sender, EventArgs e)
        {
            /*if (textBox2.Text.Length == 0)
          {
              MessageBox.Show("El tamaño de la matriz es nula", "Error");
              return;
          }
          if (textBox3.Text == null)
          {
              MessageBox.Show("La columna de la matriz es nula.", "Error");
              return;
          }
          linea2= Convert.ToInt32(textBox2.Text);
          columna2= Convert.ToInt32(textBox3.Text);*/
            if (!int.TryParse(b1.Text, out linea2))
            {
                MessageBox.Show("La linea de la matriz  es nula.", "Error");
                return;
            }
            if (!int.TryParse(b2.Text, out columna2))
            {
                MessageBox.Show("La columna de la segunda matriz es nula.", "Error");
                return;
            }
            matriz2 = new TextBox[linea2, columna2];
            int TamanhoText = groupBoxMatriz2.Width / columna2;
            for (int x = 0; x < matriz2.GetLength(0); x++)
            {
                for (int y = 0; y < matriz2.GetLength(1); y++)
                {
                    matriz2[x, y] = new TextBox();
                    matriz2[x, y].Text = "";
                    matriz2[x, y].Top = (x * matriz2[x, y].Height) + 20;
                    matriz2[x, y].Left = y * TamanhoText + 6;
                    matriz2[x, y].Width = TamanhoText;
                    groupBoxMatriz2.Controls.Add(matriz2[x, y]);
                }
            }
        }




        private void suma_Click(object sender, EventArgs e)
        {

            if (matriz1 == null || matriz2 == null)
            {
                MessageBox.Show("matriz nula !", "Error - Array");
                return;
            }
            float[,] tempMatriz1 = new float[matriz1.GetLength(0), matriz1.GetLength(1)];
            float[,] tempMatriz2 = new float[matriz2.GetLength(0), matriz2.GetLength(1)];
            if (tempMatriz1.GetLength(0) != tempMatriz2.GetLength(0) || tempMatriz1.GetLength(1) != tempMatriz2.GetLength(1))
            {
                MessageBox.Show("solo es posible la suma de matrices del mismo orden!", "Error - Suma de matrices");
                return;
            }

            for (int x = 0; x < matriz1.GetLength(0); x++)
            {
                for (int y = 0; y < matriz1.GetLength(1); y++)
                {
                    float n = 0;
                    float.TryParse(matriz1[x, y].Text, out n);
                    tempMatriz1[x, y] = n;
                    //tempMatrix1[x, y] = Convert.ToInt32(Matrix1[x, y].Text);
                }
            }
            for (int x = 0; x < matriz2.GetLength(0); x++)
            {
                for (int y = 0; y < matriz2.GetLength(1); y++)
                {
                    float n = 0;
                    float.TryParse(matriz2[x, y].Text, out n);
                    tempMatriz2[x, y] = n;
                    //tempMatrix2[x, y] = Convert.ToInt32(matriz2[x, y].Text);
                }
            }
        }

        private void groupBox3resul_Enter(object sender, EventArgs e)
        {
        
        }

        private void button3_Click(object sender, EventArgs e)
        {
            float[,] Matrizresultemp = CalculosMatrices. suma (matriz1, matriz2);
            resultante = new TextBox[Matrizresultemp.GetLength(0), Matrizresultemp.GetLength(1)];
            int TextSize = groupBox3resul.Width / resultante.GetLength(1);
            groupBox3resul.Controls.Clear();
            for (int x = 0; x < resultante.GetLength(0); x++)
            {
                for (int y = 0; y < resultante.GetLength(1); y++)
                {
                    resultante[x, y] = new TextBox();
                    resultante[x, y].Text = Matrizresultemp[x, y].ToString();
                    resultante[x, y].Top = (x * resultante[x, y].Height) + 20;
                    resultante[x, y].Left = y * TextSize + 6;
                    resultante[x, y].Width = TextSize;
                    groupBox3resul.Controls.Add(resultante[x, y]);
                }
            }

        }




        private void crearmatriz1_Click_1(object sender, EventArgs e)
         {
             /*if (textBox1.Text.Length == 0)
           {
               MessageBox.Show("El tamaño de la matriz es nula", "Error");
               return;
           }
           if (textBox3.Text ==null)
           {
               MessageBox.Show("La columna de la matriz es nula.", "Error");
               return;
           }
           linea1 = Convert.ToInt32(textBox1.Text);
           columna1 = Convert.ToInt32(textBox3.Text);*/
            if (!int.TryParse(a1.Text, out linea1))
            {
                MessageBox.Show("La linea de la matriz 1 es nula.", "Error");
                return;
            }
            if (!int.TryParse(a2.Text, out columna1))
            {
                MessageBox.Show("La columna de la primera matriz es nula.", "Error");
                return;
            }
            matriz1 = new TextBox[linea1, columna1];
            int TamanhoText = groupBoxMatriz1.Width / columna1;
            for (int x = 0; x < matriz1.GetLength(0); x++)
            {
                for (int y = 0; y < matriz1.GetLength(1); y++)
                {
                    matriz1[x, y] = new TextBox();
                    matriz1[x, y].Text = "";
                    matriz1[x, y].Top = (x * matriz1[x, y].Height) + 20;
                    matriz1[x, y].Left = y * TamanhoText + 6;
                    matriz1[x, y].Width = TamanhoText;
                    groupBoxMatriz1.Controls.Add(matriz1[x, y]);
                }
            }

        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }
    }
}
