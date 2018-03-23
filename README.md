# Examen_Unidad1
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Examen1 extends JFrame {

    private  JButton btn,btn2,btn3;
    private JTextField txt;
    private  JComboBox<Integer> cb1;
    private JComboBox<Integer> cb2;
    private JComboBox<Integer> cb3;
    private JLabel label1;
    private JLabel label2;
    private JLabel label3;

    public Examen1() {

        //Titulo de la ventana a mostrar
        super("Calculo de Velocidad");

        //Creación del boton para presionar y calcular
        btn = new JButton("Calcular Velocidad");
        btn2 = new JButton("Calcular Tiempo");
        btn3 = new JButton("Calcular Distancia");
        //creación del textfield
        txt = new JTextField(10);
        txt.setEditable(false);

        //creacion de JcomoBox para Tener los números de 1 al 100 para poder calcular la velocidad con base
        //a las distancia y tiempo dado
        cb1 = new JComboBox<>();
        cb2 = new JComboBox<>();
        cb3 = new JComboBox<>();

        //Creacion de los labels para identificar que indica cada número
        label1 = new JLabel("Distancia");
        label2 = new JLabel("Tiempo");
        label3 = new JLabel("Velocidad");

        //Agregacion de las variables creadas para agregar al contendor Principal con su layout respectivo
        getContentPane().setLayout(new GridLayout(5, 2));

        //Agregar en el gridLayout
        getContentPane().add(label1);
        getContentPane().add(cb1);
        getContentPane().add(label2);
        getContentPane().add(cb2);
        getContentPane().add(label3);
        getContentPane().add(cb3);
        getContentPane().add(btn);
        getContentPane().add(btn2);
        getContentPane().add(btn3);
        getContentPane().add(txt);

        //creacion de un for para que el usuario pueda escoger entre esos números
        for (int i = 0; i <= 100; i++) {
            cb1.addItem(Integer.valueOf(i));
            cb2.addItem(Integer.valueOf(i));
            cb3.addItem(Integer.valueOf(i));
        }

        //Creacion de oyente para el botón
        ActionListener oyenteBtnCalc2= new ActionBtnCalc();
        ActionListener oyenteBtnCalc3 = new ActionBtnCalc();
        ActionListener oyenteBtnCalc =new ActionBtnCalc();
        //Vínculo de boton con click
        btn.addActionListener(oyenteBtnCalc);
        btn2.addActionListener(oyenteBtnCalc2);
        btn3.addActionListener(oyenteBtnCalc3);

    }

    class ActionBtnCalc implements ActionListener {
        @Override
        public void actionPerformed(ActionEvent e) {
            System.out.println("Presionaste el boton : " + ((JButton) e.getSource()).getText());

            // se crea las variables para lo selecionado del JComboBox
            Integer distance = (Integer) cb1.getSelectedItem();
            Integer time = (Integer) cb2.getSelectedItem();
            Integer velocity= (Integer) cb3.getSelectedItem();
            if(e.getSource().equals(btn))
            {
                //Se crea la variable de velocidad para calcular y convirtiendolo a double la respuesta
                double Velocidad = (double) distance.intValue()/time.intValue();
                //en el textField se agrega la respuesta ya de haberse calculado
                txt.setText("velocidad-> "+Velocidad);
            }
            else if (e.getSource().equals(btn2))
            {
                //Se crea la Time de velocidad para calcular y convirtiendolo a double la respuesta
                double Time = (double) distance.intValue()/velocity.intValue();
                //en el textField se agrega la respuesta ya de haberse calculado
                txt.setText("tiempo-> "+Time);
            }
            else if(e.getSource().equals(btn3))
            {
                //Se crea la Distance de velocidad para calcular y convirtiendolo a double la respuesta
                double Distance = (double) time.intValue()*velocity.intValue();
                //en el textField se agrega la respuesta ya de haberse calculado
                txt.setText("distancia-> "+Distance);
            }

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
