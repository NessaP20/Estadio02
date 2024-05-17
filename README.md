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

        while (elegir < 1 || elegir > artistas.Length)
        {
            Console.WriteLine("Selección inválida. Por favor, elige un número entre 1 y " + artistas.Length + ".");
            Console.WriteLine("Selecciona qué artista deseas ir a ver en concierto:");
            elegir = int.Parse(Console.ReadLine());
        }
