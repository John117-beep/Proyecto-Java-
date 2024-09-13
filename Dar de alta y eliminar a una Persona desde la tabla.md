import javax.swing.*;
import javax.swing.table.DefaultTableModel;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class UniversidadApp extends JFrame {
    // Elementos de la interfaz
    private DefaultTableModel tableModel;
    private JTable table;
    private JButton altaButton, eliminarButton, modificarButton, buscarButton, RegresarButton;
    private JLabel adminLabel, usuarioLabel, contraseñaLabel, departamentoLabel;
    private JComboBox<String> adminComboBox, departamentoComboBox;

    public UniversidadApp() {
        // Configuración de la ventana
        setTitle("Gestión de Alumnos");
        setSize(600, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null); // Centra la ventana en la pantalla

        // Creación de la tabla y su modelo de datos
        tableModel = new DefaultTableModel();
        tableModel.addColumn("Nombre Completo");
        tableModel.addColumn("Usuario");
        tableModel.addColumn("Tipo de Usuario");
        tableModel.addColumn("Contraseña");
        tableModel.addColumn("Departamento");

        table = new JTable(tableModel);

        // Inicialización de los elementos de la interfaz
        altaButton = new JButton("Alta");
        eliminarButton = new JButton("Eliminar");
        modificarButton = new JButton("Modificar");
        buscarButton = new JButton("Buscar");
        RegresarButton = new JButton ("Regresar");

        adminLabel = new JLabel("Administrador:");
        usuarioLabel = new JLabel("Usuario:");
        contraseñaLabel = new JLabel("Contraseña:");
        departamentoLabel = new JLabel("Departamento:");

        String[] adminOptions = {"Admin1", "Admin2"}; // Opciones de administrador
        adminComboBox = new JComboBox<>(adminOptions);

        String[] departamentoOptions = {"R.R.H.H", "Otro Departamento,"};
        departamentoComboBox = new JComboBox<>(departamentoOptions);

        // Configuración del diseño
        setLayout(new BorderLayout());

        JPanel topPanel = new JPanel();
        topPanel.setLayout(new FlowLayout(FlowLayout.LEFT));
        topPanel.add(adminLabel);
        topPanel.add(adminComboBox);
        topPanel.add(usuarioLabel);
        topPanel.add(contraseñaLabel);
        topPanel.add(departamentoLabel);
        topPanel.add(departamentoComboBox);

        JPanel buttonPanel = new JPanel();
        buttonPanel.setLayout(new FlowLayout(FlowLayout.LEFT));
        buttonPanel.add(altaButton);
        buttonPanel.add(eliminarButton);
        buttonPanel.add(modificarButton);
        buttonPanel.add(buscarButton);
        buttonPanel.add(RegresarButton);
        add(topPanel, BorderLayout.NORTH);
        add(new JScrollPane(table), BorderLayout.CENTER);
        add(buttonPanel, BorderLayout.SOUTH);

        // Manejadores de eventos para los botones
        altaButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                // Agregar fila a la tabla con datos de ejemplo
                tableModel.addRow(new Object[]{});
            }
        });

        eliminarButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                // Eliminar fila seleccionada de la tabla
                int selectedRow = table.getSelectedRow();
                if (selectedRow != -1) {
                    tableModel.removeRow(selectedRow);
                } else {
                    JOptionPane.showMessageDialog(UniversidadApp.this, "Por favor seleccione una fila para eliminar.", "Error", JOptionPane.ERROR_MESSAGE);
                }
            }
        });

        modificarButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                // Modificar fila seleccionada de la tabla
                int selectedRow = table.getSelectedRow();
                if (selectedRow != -1) {
                    // Por simplicidad, aquí puedes abrir un diálogo para editar los datos de la fila seleccionada
                    JOptionPane.showMessageDialog(UniversidadApp.this, "Función de modificación no implementada en este ejemplo.", "Información", JOptionPane.INFORMATION_MESSAGE);
                } else {
                    JOptionPane.showMessageDialog(UniversidadApp.this, "Por favor seleccione una fila para modificar.", "Error", JOptionPane.ERROR_MESSAGE);
                }
            }
        });

        buscarButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                // Por simplicidad, aquí puedes agregar funcionalidad para buscar en la tabla
                JOptionPane.showMessageDialog(UniversidadApp.this, "Función de búsqueda no implementada en este ejemplo.", "Información", JOptionPane.INFORMATION_MESSAGE);
            }
        });
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            UniversidadApp app = new UniversidadApp();
            app.setVisible(true);
        });
    }
}
