using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;

namespace Calculator
{
    public partial class Form1 : Form
    {
        string operation = "";
        double value = 0;
        bool operation_pressed = false;

        public Form1()
        {
            InitializeComponent();
        }

        private void button15_Click(object sender, EventArgs e)
        {
            if ((result.Text == "0") || operation_pressed) {
                result.Clear();
            }
            operation_pressed = false;

            Button b = (Button)sender;
            result.Text += b.Text;
        }

        private void button17_Click(object sender, EventArgs e)
        {
            if (!String.IsNullOrEmpty(result.Text))
            {
                Button b = (Button)sender;
                operation = b.Text; 
                value = Double.Parse(result.Text); 
                operation_pressed = true;
            }
        }

        private void button18_Click(object sender, EventArgs e)
        {
            switch (operation) { 
                case "+":
                    result.Text = (value + Double.Parse(result.Text)).ToString();
                    break;
                case "-":
                    result.Text = (value - Double.Parse(result.Text)).ToString();
                    break;
                case "*":
                    result.Text = (value * Double.Parse(result.Text)).ToString();
                    break;
                case "/":
                    result.Text = (value / Double.Parse(result.Text)).ToString();
                    break;
                //default:
                   // MessageBox.Show("Empty operation..");
                   // break;
            }

            if (!String.IsNullOrEmpty(result.Text))
            {
                value = Double.Parse(result.Text);
            }
                operation = "";
                operation_pressed = true;
            

        }

        private void button5_Click(object sender, EventArgs e)
        {
            if (result.Text.Length > 0)
            {
                result.Text = result.Text.Remove(result.Text.Length - 1);
            }
        }

        private void button16_Click(object sender, EventArgs e)
        {
            if (result.Text.Length > 0 && !result.Text.Contains(","))
            {
                result.Text = (Double.Parse(result.Text) + ",").ToString();
            }
        }

        private void button10_Click(object sender, EventArgs e)
        {
            result.Clear();
        }

      
    }
}
