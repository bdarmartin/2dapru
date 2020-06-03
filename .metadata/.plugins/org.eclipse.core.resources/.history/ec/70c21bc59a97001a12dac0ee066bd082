package gt.edu.umg.progra1.ejemplo;

import java.awt.EventQueue;

import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.border.EmptyBorder;
import javax.swing.table.DefaultTableModel;
import javax.swing.JTable;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JTextField;
import javax.swing.JButton;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

public class FrmTabla extends JFrame {

	/**
	 * 
	 */
	private static final long serialVersionUID = 1L;
	private JPanel contentPane;
	private JTable table;
	private JTextField txtNombre;
	private JTextField txtColor;
	private DefaultTableModel tableModel;

	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					FrmTabla frame = new FrmTabla();
					frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}
	
	public int getSumaAscii(String linea) {
		int total = 0;
		for (int i = 0; i < linea.length(); i++) {
			char c = linea.charAt(i);
			int ascii = (int) c;
			total += ascii;
		}
		int id = (total % 50);
		return id;
	}
	
	private boolean verificarColosion(int id) {
		boolean existe = false;
		for (int i = 0; i < tableModel.getRowCount(); i++) {
			String valor = tableModel.getValueAt(i, 0).toString();
			if (id == Integer.parseInt(valor)) {
				existe = true;
				break;
			}
		}
		return existe;
	}

	/**
	 * Create the frame.
	 */
	public FrmTabla() {
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 450, 300);
		contentPane = new JPanel();
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
		setContentPane(contentPane);
		contentPane.setLayout(null);
		tableModel = new DefaultTableModel();
		tableModel.addColumn("ID");
		tableModel.addColumn("Nombre");
		tableModel.addColumn("Color");
		table = new JTable();
		table.setBounds(12, 126, 426, 133);
		table.setModel(tableModel);
		contentPane.add(table);
		
		JLabel lblNombre = new JLabel("Nombre");
		lblNombre.setBounds(39, 12, 55, 14);
		contentPane.add(lblNombre);
		
		txtNombre = new JTextField();
		txtNombre.setBounds(33, 43, 114, 18);
		contentPane.add(txtNombre);
		txtNombre.setColumns(10);
		
		JLabel lblColor = new JLabel("Color");
		lblColor.setBounds(39, 69, 55, 14);
		contentPane.add(lblColor);
		
		txtColor = new JTextField();
		txtColor.setBounds(33, 95, 114, 18);
		contentPane.add(txtColor);
		txtColor.setColumns(10);
		
		JButton btnAgregar = new JButton("Agregar");
		btnAgregar.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				int id = getSumaAscii(txtNombre.getText().trim());
				if (verificarColosion(id)) {
					JOptionPane.showMessageDialog(null, "La fruta ya existe en la lista", "Duplicidad de informacion", JOptionPane.ERROR_MESSAGE);
				} else {
					Fruta f = new Fruta();
					f.setId(id);
					f.setNombre(txtNombre.getText().trim());
					f.setColor(txtColor.getText().trim());
					tableModel.addRow(new Object[] {f.getId(), f.getNombre(), f.getColor()});
					txtNombre.setText("");
					txtColor.setText("");
				}
			}
		});
		btnAgregar.setBounds(340, 92, 98, 24);
		contentPane.add(btnAgregar);
	}
}