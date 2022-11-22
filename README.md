Ing System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Proyetofinal
{
    internal class Program
    {
        static void Main(string[] args)
        {


            string nombreUsuario;

            int tipoPizza;
            int tamanioPizza;
            int masaPizza;
            int ingredientePizza;

            int totalPizzasComprar;
            int tPizzas;

            string confirmacion, nombreCliente;

            int precioTotalPizza;

            int cClientes;

            int todosAtendidos = 0;

            Random rd = new Random();

            //tipos Pizza
            string[] vectorTipoPizza = new string[3]{ "Pepperoni", "Hawaina", "Jamon" };
            int[] vectorTipoPizzaPrecio = new int[3]{ 10, 20, 30 };

            //tamanios Pizza
            string[] vectorTamanioPizza = new string[3]{ "Personal", "Mediana", "Grande" };
            int[] vectorTamanioPrecio = new int[3]{ 40, 30, 50 };

            //masa Pizza
            string[] vectorMasaPizza = new string[2]{ "Delgada", "Gruesa" };
            int[] vectorMasaPizzaPrecio = new int[2]{ 60, 70 };

            //ingredientes Pizza
            string[] vectorIngredientesPizza = new string[3]{ "Queso", "hongos", "anchoas" };
            int[] vectorIngredientesPizzaPrecio = new int[3]{ 80, 90, 100 };


            //ingreso de clientes
            do
            {
                Console.WriteLine("Cuantos clientes desea atender?: ");
                cClientes = int.Parse(Console.ReadLine());
                Console.WriteLine("");
                Console.WriteLine("");

                if (cClientes <= 0)
                {
                    Console.WriteLine("Atención, debe de ingresar al menos un nombre para poder seguir!");
                    Console.ReadKey();
                    Console.Clear();
                }

            } while (cClientes <= 0);

            Console.Clear();

            string[, ] vectorCantidadClientes = new string[cClientes, 2];

            for (int i = 0; i < cClientes; i++)
            {
                Console.WriteLine("----------" + "Ingreso de cliente no. " + (i + 1) + "----------");
                Console.WriteLine("Ingreso el nombre del cliente: ");
                nombreCliente = Console.ReadLine();
                vectorCantidadClientes[i, 0] = nombreCliente;
                vectorCantidadClientes[i, 1] = "N";
                Console.WriteLine("----------" + "Ingreso de cliente no. " + (i + 1) + " Finalizado ----------");
                Console.ReadKey();
                Console.Clear();
            }

            Console.WriteLine("----------" + "Los cliente para atender son:" + "----------");
            Console.WriteLine("");
            for (int i = 0; i < cClientes; i++)
            {
                if (vectorCantidadClientes[i, 1] == "N")
                {
                    Console.WriteLine("Nombre: " + vectorCantidadClientes[i, 0] + " -> Pendiente de atender");
                }
            }

            Console.WriteLine("");
            Console.WriteLine("Presione ENTER para continuar");
            Console.ReadKey();
            Console.Clear();

            //-------------------------Fin ingreso de clientes-------------------------


            do
            {
                int random = rd.Next(0, cClientes - 1);


                if (vectorCantidadClientes[random, 1] == "N")
                {

                    nombreUsuario = vectorCantidadClientes[random, 0];

                    //-----------------------------------------------------------------------------------------
                    //Cantidades de Pizzas

                    do
                    {
                        Console.WriteLine("Ingrese la cantidad de pizzas a comprar " + nombreUsuario + ": ");
                        totalPizzasComprar = int.Parse(Console.ReadLine());
                        Console.WriteLine("");
                        Console.WriteLine("");

                        if (totalPizzasComprar <= 0)
                        {
                            Console.WriteLine("Usted debe comprar al menos 1 pizza");
                            Console.ReadKey();
                        }

                    } while (totalPizzasComprar <= 0);

                    //Inicializando la variable tPizzas
                    tPizzas = 0;


                    do
                    {
                        //Tipo Pizza

                        Console.Clear();

                        Console.WriteLine("---------------------Realice su pedido para la pizza no. " + (tPizzas + 1) + "-------------------------------");

                        Console.WriteLine("---> " + nombreUsuario + ", por favor seleccione el tipo de Pizza: ");
                        Console.WriteLine("");

                        for (int i = 0; i <= vectorTipoPizza.Length - 1; i++)
                        {
                            Console.WriteLine((i + 1) + " - " + vectorTipoPizza[i] + " / Q. " + vectorTipoPizzaPrecio[i]);
                        }

                        tipoPizza = int.Parse(Console.ReadLine());

                        while (tipoPizza < 1 || tipoPizza > 3)
                        {
                            Console.WriteLine("");
                            Console.WriteLine("Usted no seleccionó un valor correcto, por favor intente de nuevo");
                            tipoPizza = int.Parse(Console.ReadLine());
                        }
                        Console.WriteLine("Tipo de Pizza almacenado!");
                        Console.WriteLine("");
                        Console.WriteLine("");


                        //Tamanio Pizza
                        Console.WriteLine("---> " + nombreUsuario + ", por favor seleccione el tamaño de Pizza: ");
                        Console.WriteLine("");

                        for (int i = 0; i <= vectorTamanioPizza.Length - 1; i++)
                        {
                            Console.WriteLine((i + 1) + " - " + vectorTamanioPizza[i] + " / Q. " + vectorTamanioPrecio[i]);
                        }

                        tamanioPizza = int.Parse(Console.ReadLine());

                        while (tamanioPizza < 1 || tamanioPizza > 3)
                        {
                            Console.WriteLine("");
                            Console.WriteLine("Usted no seleccionó un valor correcto, por favor intente de nuevo");
                            tamanioPizza = int.Parse(Console.ReadLine());
                        }
                        Console.WriteLine("Tamaño de Pizza almacenado!");
                        Console.WriteLine("");
                        Console.WriteLine("");


                        //Masa Pizza
                        Console.WriteLine("---> " + nombreUsuario + ", por favor seleccione la masa de la Pizza: ");
                        Console.WriteLine("");

                        for (int i = 0; i <= vectorMasaPizza.Length - 1; i++)
                        {
                            Console.WriteLine((i + 1) + " - " + vectorMasaPizza[i] + " / Q. " + vectorMasaPizzaPrecio[i]);
                        }

                        masaPizza = int.Parse(Console.ReadLine());

                        while (masaPizza < 1 || masaPizza > 2)
                        {
                            Console.WriteLine("");
                            Console.WriteLine("Usted no seleccionó un valor correcto, por favor intente de nuevo");
                            masaPizza = int.Parse(Console.ReadLine());
                        }
                        Console.WriteLine("Masa de la Pizza almacenado!");
                        Console.WriteLine("");
                        Console.WriteLine("");


                        //Ingredientes Pizza
                        Console.WriteLine("---> " + nombreUsuario + ", por favor seleccione el ingrediente extra de la Pizza: ");
                        Console.WriteLine("");

                        for (int i = 0; i <= vectorIngredientesPizza.Length - 1; i++)
                        {
                            Console.WriteLine((i + 1) + " - " + vectorIngredientesPizza[i] + " / Q. " + vectorIngredientesPizzaPrecio[i]);
                        }

                        ingredientePizza = int.Parse(Console.ReadLine());

                        while (ingredientePizza < 1 || ingredientePizza > 3)
                        {
                            Console.WriteLine("");
                            Console.WriteLine("Usted no seleccionó un valor correcto, por favor intente de nuevo");
                            ingredientePizza = int.Parse(Console.ReadLine());
                        }
                        Console.WriteLine("Ingrediente de la Pizza almacenado!");
                        Console.WriteLine("");
                        Console.WriteLine("");


                        Console.WriteLine("¡Ingreso de pizza terminado!");
                        Console.WriteLine("");

                        Console.WriteLine("Tipo de Pizza: " + vectorTipoPizza[tipoPizza - 1] + " Q. " + vectorTipoPizzaPrecio[tipoPizza - 1]);
                        Console.WriteLine("Tamaño de Pizza: " + vectorTamanioPizza[tamanioPizza - 1] + " Q. " + vectorTamanioPrecio[tamanioPizza - 1]);
                        Console.WriteLine("Masa de Pizza: " + vectorMasaPizza[masaPizza - 1] + " Q. " + vectorMasaPizzaPrecio[masaPizza - 1]);
                        Console.WriteLine("Ingreedientes extra de Pizza: " + vectorIngredientesPizza[ingredientePizza - 1] + " Q. " + vectorIngredientesPizzaPrecio[ingredientePizza - 1]);
                        Console.WriteLine("");

                        precioTotalPizza = vectorTipoPizzaPrecio[tipoPizza - 1] + vectorTamanioPrecio[tamanioPizza - 1] + vectorMasaPizzaPrecio[masaPizza - 1] + vectorIngredientesPizzaPrecio[ingredientePizza - 1];
                        Console.WriteLine("Su total es: Q." + precioTotalPizza);

                        Console.WriteLine("");
                        Console.WriteLine("");
                        Console.WriteLine("¿Desea confirmar su pediddo? S (Si) / Cualquier otra tecla para no");
                        confirmacion = Console.ReadLine();

                        if (confirmacion != "S" && confirmacion != "s")
                        {
                            Console.Write("Pedido cancelado!");
                            Console.ReadKey();
                        }

                        tPizzas++;

                    } while ((confirmacion == "S" || confirmacion == "s") && tPizzas < totalPizzasComprar);

                    Console.Clear();

                    vectorCantidadClientes[random, 1] = "S";


                    //-----------------------------------------------------------------------------------------


                    todosAtendidos++;
                }
                else
                {

                    for (int i = 0; i < cClientes; i++)
                    {
                        if (vectorCantidadClientes[i, 1] != "N")
                        {
                            todosAtendidos = 0;
                        }
                    }

                }



            } while (todosAtendidos != 1);


        }
    }

