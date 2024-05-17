class Estadio
{
    static void Main(string[] args)
    {
        string nombre;
        int elegir;
        int entradas = 0;
        string[] zona = new string[3];
        int eleccion, filaSeleccionada, columnaSeleccionada;
        string[] zonas = { "1.Preferente", "2.Tribuna", "3.Platea" };
        char[,] asientos = new char[8, 5];
        char[,] asiento = new char[5, 8];

        int precioPreferente = 62;
        int precioTribuna = 75;
        int precioPlatea = 80;

        Console.WriteLine("Bienvenido a TicketArena");
        Console.WriteLine("Cual es tu nombre?");
        nombre = Console.ReadLine();

        string[] artistas = { "Chayanne", "Morat" };

        Console.WriteLine(nombre + " " + "te mostramos las funciones disponibles en este mes:");

        Console.WriteLine("1." + " " + artistas[0] + " " + "08/06/24");
        Console.WriteLine("2." + " " + artistas[1] + " " + "21/06/24");

        Console.WriteLine("Selecciona que artista deseas ir a ver en concierto");
        elegir = int.Parse(Console.ReadLine());
        switch (elegir)
{
    case 1:

        while (entradas <= 0)
        {
            Console.WriteLine("Ingrese el número de asientos que desea reservar");
            entradas = int.Parse(Console.ReadLine());

            if (entradas <= 0)
            {
                Console.WriteLine("Número invalido, por favor ingrese otro valor");

            }
            else
            {
                Console.WriteLine("Usted a reservado" + " " + entradas + "  " + "entradas");
            }
        }

        Console.WriteLine("Te mostramos las zonas disponibles y sus respectivos precios");
        Console.WriteLine();
        Console.WriteLine(zonas[0] + " " + "$62");
        Console.WriteLine(zonas[1] + "  " + "$75");
        Console.WriteLine(zonas[2] + " " + "$80");
        Console.WriteLine();
        Console.WriteLine("Seleccione la zona en la que desea reservar su asiento:");
        eleccion = int.Parse(Console.ReadLine());

        while (elegir < 1 || elegir > artistas.Length)
        {
            Console.WriteLine("Selección inválida. Por favor, elige un número entre 1 y " + artistas.Length + ".");
            Console.WriteLine("Selecciona qué artista deseas ir a ver en concierto:");
            elegir = int.Parse(Console.ReadLine());
        }

        switch (eleccion)
                {
                    case 1:

                        for (int i = 0; i < 8; i++)
                        {
                            for (int j = 0; j < 5; j++)
                            {
                                asientos[i, j] = '*';
                            }
                        }

                        Console.WriteLine("Seleccione el asiento de su preferencia:");
                        Console.WriteLine("  1 2 3 4 5 ");

                        for (int i = 0; i < 8; i++)
                        {
                            Console.Write((char)('A' + i) + " ");
                            for (int j = 0; j < 5; j++)
                            {
                                Console.Write(asientos[i, j] + " ");
                            }
                            Console.WriteLine();
                        }

                        while (true)
                        {
                            Console.WriteLine("\nIngrese los asientos que desea seleccionar separados por comas (por ejemplo, A3,A4,B5,C6):");
                            string input = Console.ReadLine().ToUpper();

                            string[] asientosSeleccionados = input.Split(',');

                            if (asientosSeleccionados.Length != entradas)
                            {
                                Console.WriteLine("Debe seleccionar exactamente " + entradas + " asientos.");
                                continue;
                            }

                            for (int k = 0; k < asientosSeleccionados.Length; k++)
                            {
                                string asientoSeleccionado = asientosSeleccionados[k];

                                if (asientoSeleccionado.Length != 2 || !char.IsLetter(asientoSeleccionado[0]) || !char.IsDigit(asientoSeleccionado[1]))
                                {
                                    Console.WriteLine("Entrada no válida. Por favor, ingrese los asientos en el formato correcto (A-E1-5).");
                                    continue;
                                }

                                filaSeleccionada = asientoSeleccionado[0] - 'A';
                                columnaSeleccionada = asientoSeleccionado[1] - '1';

                                if (filaSeleccionada < 0 || filaSeleccionada >= 8 || columnaSeleccionada < 0 || columnaSeleccionada >= 5)
                                {
                                    Console.WriteLine("El asiento seleccionado está fuera de los límites.");
                                    continue;
                                }

                                asientos[filaSeleccionada, columnaSeleccionada] = 'O';
                            }

                            Console.WriteLine("Seleccione el asiento de su preferencia:");
                            Console.WriteLine("  1 2 3 4 5 ");

                            for (int i = 0; i < 8; i++)
                            {
                                Console.Write((char)('A' + i) + " ");
                                for (int j = 0; j < 5; j++)
                                {
                                    if (asientos[i, j] == 'O')
                                    {
                                        Console.ForegroundColor = ConsoleColor.Green;
                                    }
                                    Console.Write(asientos[i, j] + " ");
                                    Console.ResetColor();
                                }
                                Console.WriteLine();
                            }


                            Console.WriteLine("Tu total a pagar es:" + " $" + entradas * 62);
                            Console.WriteLine("Ingresa tu numero de tarjeta para pagar");
                            int pago = int.Parse(Console.ReadLine());
                            Console.WriteLine("Gracias por la compra!");

                            return;

                        }

                        break;

                     case 2:
                        {
                            for (int i = 0; i < 5; i++)
                            {
                                for (int j = 0; j < 8; j++)
                                {
                                    asiento[i, j] = '*';
                                }
                            }

                            Console.WriteLine("Estado de los asientos:");
                            Console.WriteLine("  1 2 3 4 5 6 7 8 ");

                            for (int i = 0; i < 5; i++)
                            {
                                Console.Write((char)('A' + i) + " ");
                                for (int j = 0; j < 8; j++)
                                {
                                    Console.Write(asiento[i, j] + " ");
                                }
                                Console.WriteLine();
                            }

                            while (true)
                            {
                                Console.WriteLine("\nIngrese los asientos que desea seleccionar separados por comas (por ejemplo, A3,A4,B5,C6):");
                                string input = Console.ReadLine().ToUpper();

                                string[] asientosSeleccionados = input.Split(',');

                                if (asientosSeleccionados.Length != entradas)
                                {
                                    Console.WriteLine("Debe seleccionar exactamente " + entradas + " asientos.");
                                    continue;
                                }

                                for (int k = 0; k < asientosSeleccionados.Length; k++)
                                {
                                    string asientoSeleccionado = asientosSeleccionados[k];

                                    if (asientoSeleccionado.Length != 2 || !char.IsLetter(asientoSeleccionado[0]) || !char.IsDigit(asientoSeleccionado[1]))
                                    {
                                        Console.WriteLine("Entrada no válida. Por favor, ingrese los asientos en el formato correcto (A-E1-5).");
                                        continue;
                                    }

                                    filaSeleccionada = asientoSeleccionado[0] - 'A';
                                    columnaSeleccionada = asientoSeleccionado[1] - '1';

                                    if (filaSeleccionada < 0 || filaSeleccionada >= 5 || columnaSeleccionada < 0 || columnaSeleccionada >= 8)
                                    {
                                        Console.WriteLine("El asiento seleccionado está fuera de los límites.");
                                        continue;
                                    }

                                    asiento[filaSeleccionada, columnaSeleccionada] = 'O';
                                }

                                Console.WriteLine("\nEstado de los asientos:");
                                Console.WriteLine("  1 2 3 4 5 6 7 8 ");

                                for (int i = 0; i < 5; i++)
                                {
                                    Console.Write((char)('A' + i) + " ");
                                    for (int j = 0; j < 8; j++)
                                    {
                                        if (asiento[i, j] == 'O')
                                        {
                                            Console.ForegroundColor = ConsoleColor.Green;
                                        }
                                        Console.Write(asiento[i, j] + " ");
                                        Console.ResetColor();
                                    }
                                    Console.WriteLine();
                                }


                                Console.WriteLine("Tu total a pagar es:" + " $" + entradas * 75);
                                Console.WriteLine("Ingresa tu numero de tarjeta para pagar");
                                int pago = int.Parse(Console.ReadLine());
                                Console.WriteLine("Gracias por la compra!");

                                return;

                            }
                        }

                    case 3:
                        {
                            for (int i = 0; i < 5; i++)
                            {
                                for (int j = 0; j < 5; j++)
                                {
                                    asiento[i, j] = '*';
                                }
                            }
                            Console.WriteLine("Estado de los asientos:");
                            Console.WriteLine("  1 2 3 4 5 ");

                            for (int i = 0; i < 5; i++)
                            {
                                Console.Write((char)('A' + i) + " ");
                                for (int j = 0; j < 5; j++)
                                {
                                    Console.Write(asiento[i, j] + " ");
                                }
                                Console.WriteLine();
                            }

                            while (true)
                            {
                                Console.WriteLine("\nIngrese los asientos que desea seleccionar separados por comas (por ejemplo, A3,A4,B5,C6):");
                                string input = Console.ReadLine().ToUpper();

                                string[] asientosSeleccionados = input.Split(',');

                                if (asientosSeleccionados.Length != entradas)
                                {
                                    Console.WriteLine("Debe seleccionar exactamente " + entradas + " asientos.");
                                    continue;
                                }

                                for (int k = 0; k < asientosSeleccionados.Length; k++)
                                {
                                    string asientoSeleccionado = asientosSeleccionados[k];

                                    if (asientoSeleccionado.Length != 2 || !char.IsLetter(asientoSeleccionado[0]) || !char.IsDigit(asientoSeleccionado[1]))
                                    {
                                        Console.WriteLine("Entrada no válida. Por favor, ingrese los asientos en el formato correcto (A-E1-5).");
                                        continue;
                                    }

                                    filaSeleccionada = asientoSeleccionado[0] - 'A';
                                    columnaSeleccionada = asientoSeleccionado[1] - '1';

                                    if (filaSeleccionada < 0 || filaSeleccionada >= 5 || columnaSeleccionada < 0 || columnaSeleccionada >= 5)
                                    {
                                        Console.WriteLine("El asiento seleccionado está fuera de los límites.");
                                        continue;
                                    }

                                    asiento[filaSeleccionada, columnaSeleccionada] = 'O';
                                }

                                Console.WriteLine("\nEstado de los asientos:");
                                Console.WriteLine("  1 2 3 4 5 ");

                                for (int i = 0; i < 5; i++)
                                {
                                    Console.Write((char)('A' + i) + " ");
                                    for (int j = 0; j < 5; j++)
                                    {
                                        if (asiento[i, j] == 'O')
                                        {
                                            Console.ForegroundColor = ConsoleColor.Green;
                                        }
                                        Console.Write(asiento[i, j] + " ");
                                        Console.ResetColor();
                                    }
                                    Console.WriteLine();
                                }


                                Console.WriteLine("Tu total a pagar es:" + " $" + entradas * 80);
                                Console.WriteLine("Ingresa tu numero de tarjeta para pagar");
                                int pago = int.Parse(Console.ReadLine());
                                Console.WriteLine("Gracias por la compra!");

                                return;

                            }
                        }
                         case 2:

     while (entradas <= 0)
     {
         Console.WriteLine("Ingrese el número de asientos que desea reservar");
         entradas = int.Parse(Console.ReadLine());

         if (entradas <= 0)
         {
             Console.WriteLine("Número invalido, por favor ingrese otro valor");

         }
         else
         {
             Console.WriteLine("Usted a reservado" + " " + entradas + "  " + "entradas");
         }
     }

                Console.WriteLine("Te mostramos las zonas disponibles y sus respectivos precios");
                Console.WriteLine();
                Console.WriteLine(zonas[0] + " " + "$62");
                Console.WriteLine(zonas[1] + "  " + "$75");
                Console.WriteLine(zonas[2] + " " + "$80");
                Console.WriteLine();
                Console.WriteLine("Seleccione la zona en la que desea reservar su asiento:");
                eleccion = int.Parse(Console.ReadLine());

                }

                break;

                switch (eleccion)
                {
                    case 1:

                        for (int i = 0; i < 8; i++)
                        {
                            for (int j = 0; j < 5; j++)
                            {
                                asientos[i, j] = '*';
                            }
                        }

                        Console.WriteLine("Seleccione el asiento de su preferencia:");
                        Console.WriteLine("  1 2 3 4 5 ");

                        for (int i = 0; i < 8; i++)
                        {
                            Console.Write((char)('A' + i) + " ");
                            for (int j = 0; j < 5; j++)
                            {
                                Console.Write(asientos[i, j] + " ");
                            }
                            Console.WriteLine();
                        }

                        while (true)
                        {
                            Console.WriteLine("\nIngrese los asientos que desea seleccionar separados por comas (por ejemplo, A3,A4,B5,C6):");
                            string input = Console.ReadLine().ToUpper();

                            string[] asientosSeleccionados = input.Split(',');

                            if (asientosSeleccionados.Length != entradas)
                            {
                                Console.WriteLine("Debe seleccionar exactamente " + entradas + " asientos.");
                                continue;
                            }

                            for (int k = 0; k < asientosSeleccionados.Length; k++)
                            {
                                string asientoSeleccionado = asientosSeleccionados[k];

                                if (asientoSeleccionado.Length != 2 || !char.IsLetter(asientoSeleccionado[0]) || !char.IsDigit(asientoSeleccionado[1]))
                                {
                                    Console.WriteLine("Entrada no válida. Por favor, ingrese los asientos en el formato correcto (A-E1-5).");
                                    continue;
                                }

                                filaSeleccionada = asientoSeleccionado[0] - 'A';
                                columnaSeleccionada = asientoSeleccionado[1] - '1';

                                if (filaSeleccionada < 0 || filaSeleccionada >= 8 || columnaSeleccionada < 0 || columnaSeleccionada >= 5)
                                {
                                    Console.WriteLine("El asiento seleccionado está fuera de los límites.");
                                    continue;
                                }

                                asientos[filaSeleccionada, columnaSeleccionada] = 'O';
                            }

                            Console.WriteLine("Seleccione el asiento de su preferencia:");
                            Console.WriteLine("  1 2 3 4 5 ");

                            for (int i = 0; i < 8; i++)
                            {
                                Console.Write((char)('A' + i) + " ");
                                for (int j = 0; j < 5; j++)
                                {
                                    if (asientos[i, j] == 'O')
                                    {
                                        Console.ForegroundColor = ConsoleColor.Green;
                                    }
                                    Console.Write(asientos[i, j] + " ");
                                    Console.ResetColor();
                                }
                                Console.WriteLine();
                            }


                            Console.WriteLine("Tu total a pagar es:" + " $" + entradas * 62);
                            Console.WriteLine("Ingresa tu numero de tarjeta para pagar");
                            int pago = int.Parse(Console.ReadLine());
                            Console.WriteLine("Gracias por la compra!");

                            return;

                        }

                        break;


    

