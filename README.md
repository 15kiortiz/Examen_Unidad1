# Examen_Unidad1

 import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Examen1 extends JFrame {


    private  JButton btn;
    private JTextField txt;
    private  JComboBox<Integer> cb1;
    private JComboBox<Integer> cb2;
    private JLabel label1;
    private JLabel label2;


    public Examen1() {

        //Titulo de la ventana a mostrar
        super("Calculo de Velocidad");

        //Creación del boton para presionar y calcular
        btn = new JButton("Calcular");

        //creación del textfield
        txt = new JTextField(10);

        //creacion de JcomoBox para Tener los números de 1 al 100 para poder calcular la velocidad con base
        //a las distancia y tiempo dado
        cb1 = new JComboBox<>();
        cb2 = new JComboBox<>();

        //Creacion de los labels para identificar que indica cada número
        label1 = new JLabel("Distancia");
        label2 = new JLabel("Tiempo");

        //Agregacion de las variables creadas para agregar al contendor Principal con su layout respectivo
        getContentPane().setLayout(new GridLayout(0, 1));
        getContentPane().add(txt);
        getContentPane().add(btn);
        getContentPane().add(label1);
        getContentPane().add(cb1);
        getContentPane().add(label2);
        getContentPane().add(cb2);

        //creacion de un for para que el usuario pueda escoger entre esos números
        for (int i = 1; i <= 100; i++) {
            cb1.addItem(Integer.valueOf(i));
            cb2.addItem(Integer.valueOf(i));
        }

        //Creacion de oyente para el botón
        ActionListener oyenteBtnCalc =new ActionBtnCalc();
        //Vínculo de boton con click
        btn.addActionListener(oyenteBtnCalc);

    }

    class ActionBtnCalc implements ActionListener {
        @Override
        public void actionPerformed(ActionEvent e) {
            System.out.println("Presionaste el boton : " + ((JButton) e.getSource()).getText());

            // se crea las variables para lo selecionado del JComboBox
                Integer distance = (Integer) cb1.getSelectedItem();
                Integer time = (Integer) cb2.getSelectedItem();
                //Se crea la variable de velocidad para calcular y convirtiendolo a double la respuesta
                double Velocidad = (double) distance.intValue()/time.intValue();

                //en el textField se agrega la respuesta ya de haberse calculado
                txt.setText(" "+Velocidad);


        }
    }

    public static void main (String args[])
    {
        // creación de Objeto para clase Examen1
        Examen1 ventana = new Examen1();
        ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        ventana.pack();
        ventana.setVisible(true);
    }
}
