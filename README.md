import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class Dashboard extends JFrame {
    private JToolBar toolBar = new JToolBar();
    private JLabel head = new JLabel("Mobile Health View System");
    private JLabel message = new JLabel();
    private JButton Signin = new JButton("Sign In");
    private JButton Aboutus = new JButton("About Us");

    public Dashboard() {
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        setSize(width, height);
        setLocationRelativeTo(null);

        Signin.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {

                UserAccounts userAccounts = new UserAccounts();
                dispose();
            }
        });

        Aboutus.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
            AboutUs aboutUs = new AboutUs();
            dispose();
            }
        });
        toolBar.add(head);
        toolBar.addSeparator();
        toolBar.addSeparator();
        toolBar.addSeparator();
        toolBar.add(Signin);
        toolBar.addSeparator();
        toolBar.addSeparator();
        toolBar.add(Aboutus);

        JPanel backgroundPanel = new JPanel() {
            @Override
            protected void paintComponent(Graphics g) {
                super.paintComponent(g);
                ImageIcon backgroundImage = new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\resize.jpg");
                g.drawImage(backgroundImage.getImage(), 0, 0, getWidth(), getHeight(), this);

                Font labelFont = new Font("Arial", Font.BOLD, 80);
                g.setFont(labelFont);
                g.setColor(Color.BLACK);
                String label = "Health Care Simplified" ;
                int labelX = 180; // X-coordinate for the label
                int labelY = 200; // Y-coordinate for the label
                g.drawString(label, labelX, labelY);
            }
        };
        backgroundPanel.setLayout(new BorderLayout());

        JPanel panel = new JPanel();
        panel.setLayout(new BorderLayout());
        panel.add(toolBar, BorderLayout.NORTH);

        backgroundPanel.add(panel, BorderLayout.NORTH);

        add(backgroundPanel);
        setVisible(true);
    }
    public static void main(String[] args) {
        Dashboard tool = new Dashboard();
      //  dispose();
    }
}

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class AboutUs extends JFrame {
    JLabel titleLabel = new JLabel("About Us");
    JLabel locationLabel = new JLabel();
    JLabel phoneNumberLabel = new JLabel();
    JLabel emailLabel = new JLabel();
    JLabel locationLabelinfo = new JLabel("141 lilian ngoye st");
    JLabel phoneNumberLabelinfo = new JLabel("0625393078");
    JLabel emailLabelinfo = new JLabel("sagi.richfield@ca.za");
    JButton Dashb = new JButton("Dashboard");
    public AboutUs(){
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        setSize(width, height);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(null);
        setVisible(true);

        add(titleLabel);
        add(locationLabel);
        add(phoneNumberLabel);
        add(emailLabel);
        add(locationLabelinfo);
        add(phoneNumberLabelinfo);
        add(emailLabelinfo);
        add(Dashb);

        titleLabel.setFont(new Font("Arial", Font.BOLD, 20));
        titleLabel.setBounds(150, 10, 100, 30);
        //location
        locationLabel.setBounds(20, 50, 100, 50);
        locationLabel.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\location.png"));
        //phone
        phoneNumberLabel.setBounds(20, 150, 100, 50);
        phoneNumberLabel.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\telephone-call.png"));
        //email
        emailLabel.setBounds(20, 250, 100, 50);
        emailLabel.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\email.png"));
//add infor to the label
        locationLabelinfo.setBounds(150, 60, 200, 20);
        locationLabelinfo.setFont(new Font("Arial",Font.BOLD,18));
        //
        phoneNumberLabelinfo.setBounds(150, 160, 100, 20);
        phoneNumberLabelinfo.setFont(new Font("Arial",Font.BOLD,18));
        //
        emailLabelinfo.setBounds(150, 260, 300, 20);
        emailLabelinfo.setFont(new Font("Arial",Font.BOLD,18));
        Dashb.setBounds(170, 350, 100, 25);

        Dashb.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                 new Dashboard();
                 dispose();
            }
        });
    }

}

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class UserAccounts implements ActionListener {
    JFrame frame = new JFrame("UserAccounts");
    JButton ADMIN = new JButton("ADMIN LOGIN");
    JButton DOC = new JButton("DOCTOR'S LOGIN");
    JLabel Acc = new JLabel("USER ACCOUNTS");

    UserAccounts() {
        Acc.setFont(new Font("Arial", Font.BOLD, 25));
        Acc.setBounds(500, 300, 400, 40); // Set the label's position above the buttons
        Acc.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\user.png"));
        ADMIN.setBounds(400, 400, 200, 40); // Adjusted the button positions and width
        ADMIN.addActionListener(this);
        ADMIN.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\administration.png"));
        DOC.setBounds(650, 400, 200, 40); // Adjusted the button positions and width
        DOC.addActionListener(this);
        DOC.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\medical-team.png"));

        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        frame.setSize(width, height);
        frame.setLocationRelativeTo(null);
        frame.setLayout(null);
        frame.setVisible(true);

        frame.add(Acc);
        frame.add(ADMIN);
        frame.add(DOC);
    }
    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == ADMIN) {
            frame.dispose();
            new Admin();

        } else if (e.getSource() == DOC) {
            frame.dispose();
            Doctor doctor = new Doctor();
        }
    }
}
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.DriverManager;
import java.sql.*;

public class Admin extends JFrame {
    JFrame frame2 = new JFrame("Admin");
    JLabel ADminLogin = new JLabel("Admin Login");
    JLabel username = new JLabel("Username:");
    JTextField txtName = new JTextField();
    JLabel password = new JLabel("Password: ");
    JPasswordField txtPass = new JPasswordField();
    private Connection con;
    private PreparedStatement pst;
    JButton Login = new JButton("Login");

    public Admin() {
        // Set frame layout to null
        frame2.setLayout(null);

        ADminLogin.setBounds(500, 100, 400, 40);
        ADminLogin.setFont(new Font(null, Font.PLAIN, 25));
        ADminLogin.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\administration.png"));
        username.setBounds(450, 200, 100, 25);
        txtName.setBounds(600, 200, 150, 25);
        password.setBounds(450, 250, 100, 25);
        txtPass.setBounds(600, 250, 150, 25);
        Login.setBounds(600, 300, 100, 50);

        frame2.add(ADminLogin);
        frame2.add(username);
        frame2.add(txtName);
        frame2.add(password);
        frame2.add(txtPass);
        frame2.add(Login);

        frame2.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        frame2.setSize(width, height);
        frame2.setVisible(true);

        try {
            Class.forName("org.postgresql.Driver");
            con = DriverManager.getConnection("jdbc:postgresql://localhost:5432/FMS", "postgres", "Tiny@2000");
        } catch (ClassNotFoundException | SQLException ex) {
            ex.printStackTrace();
        }
        Login.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String name = txtName.getText();
                String pass = new String(txtPass.getPassword());

                if (name.isEmpty() || pass.isEmpty()) {
                    JOptionPane.showMessageDialog(null, "Both Username and Password are required.");
                } else {
                    try {
                        pst = con.prepareStatement("SELECT * FROM mytablee WHERE username = ? AND password = ?");
                        pst.setString(1, name);
                        pst.setString(2, pass);

                        ResultSet rs = pst.executeQuery();
                        if (rs.next()) {
                            frame2.dispose();
                            AdminHome homepage = new AdminHome();
                            homepage.setVisible(true);
                            setVisible(false);
                        } else {
                            JOptionPane.showMessageDialog(null, "Incorrect User");
                        }
                    } catch (SQLException ex) {
                        throw new RuntimeException(ex);
                    }
                }
            }
        });
    }
}
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.DriverManager;
import java.sql.*;

public class Doctor extends JFrame {
    JFrame frame2 = new JFrame("Doctors");
    JLabel Doctors = new JLabel("Doctors Login");
    JLabel username = new JLabel("Username:");
    JTextField txtName = new JTextField();
    JLabel password = new JLabel("Password: ");
    JPasswordField txtPass = new JPasswordField();
    private Connection con;
    private PreparedStatement pst;
    JButton Login = new JButton("Login");

    public Doctor() {
        // Set frame layout to null
        frame2.setLayout(null);
        // Set bounds for components
        Doctors.setBounds(500, 100, 400, 40);
        Doctors.setFont(new Font(null, Font.PLAIN, 25));
        Doctors.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\medical-team.png"));
        username.setBounds(450, 200, 150, 25);
        username.setFont(new Font(null, Font.PLAIN, 25));
        txtName.setBounds(600, 200, 150, 25);
        password.setBounds(450, 250, 150, 25);
        password.setFont(new Font(null, Font.PLAIN, 25));
        txtPass.setBounds(600, 250, 150, 25);
        Login.setBounds(600, 300, 100, 50);

        // Adding components to the frame
        frame2.add(Doctors);
        frame2.add(username);
        frame2.add(txtName);
        frame2.add(password);
        frame2.add(txtPass);
        frame2.add(Login);

        frame2.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        frame2.setSize(width, height);
        frame2.setVisible(true);

        // Database connection setup
        try {
            Class.forName("org.postgresql.Driver");
            con = DriverManager.getConnection("jdbc:postgresql://localhost:5432/FMS", "postgres", "Tiny@2000");
        } catch (ClassNotFoundException | SQLException ex) {
            ex.printStackTrace();
        }
        Login.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String name = txtName.getText();
                String pass = new String(txtPass.getPassword());

                if (name.isEmpty() || pass.isEmpty()) {
                    JOptionPane.showMessageDialog(null, "Both Username and Password are required.");
                } else {
                    try {
                        pst = con.prepareStatement("SELECT * FROM doctors WHERE username = ? AND password = ?");
                        pst.setString(1, name);
                        pst.setString(2, pass);

                        ResultSet rs = pst.executeQuery();
                        if (rs.next()) {
                            frame2.dispose();
                            new HomepgDoc();
                            setVisible(true);
                            setVisible(false);
                            dispose();
                        } else {
                            JOptionPane.showMessageDialog(null, "Incorrect User");
                        }
                    } catch (SQLException ex) {
                        throw new RuntimeException(ex);
                    }
                }
            }

        });
    }
}
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
public class AdminHome extends JFrame {
    JMenuBar menuBar = new JMenuBar();
    JMenu filemenu = new JMenu("Home");
    JMenuItem addNewPatientItem = new JMenuItem("New Patient");
    JMenuItem editPatientItem = new JMenuItem("View Patient");
    JMenuItem reports = new JMenuItem("Reports");
    JMenuItem Signout = new JMenuItem("Sign out");

    public AdminHome() {
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        setSize(width, height);

        // Create a JLabel to display the image
        ImageIcon backgroundImage = new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\resize.jpg"); // Replace with the path to your image
        JLabel backgroundLabel = new JLabel(backgroundImage);
        backgroundLabel.setLayout(new BorderLayout());
        setContentPane(backgroundLabel);

        // Add menu items to the patient menu
        filemenu.add(addNewPatientItem);
        filemenu.add(editPatientItem);
        filemenu.add(reports);
        filemenu.add(Signout);
        menuBar.add(filemenu);

        // Set the JMenuBar for the frame
        setJMenuBar(menuBar);
        addNewPatientItem.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                // Open the Add New Patient form
                new NewPatients();
                dispose();
            }
        });
        editPatientItem.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                // Open the Edit Patient form
                new ViewPatient();
                dispose();
            }
        });
        Signout.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                Dashboard dashboard = new Dashboard();
                dispose();
            }
        });
        reports.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                Reports reports1 = new Reports();
                dispose();
            }
        });
        setVisible(true);
    }
}

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class HomepgDoc extends JFrame {
    // Create a menu bar
    JMenuBar menuBar = new JMenuBar();
    JMenu filemenu = new JMenu("Home");
    // Create menu items
    JMenuItem edit_and_appointment = new JMenuItem("Edit and appointments");
    JMenuItem prescribe = new JMenuItem("Prescribe");
    JMenuItem Signout = new JMenuItem("Sign Out");

    public HomepgDoc() {
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        setSize(width, height);

        // Create a JLabel to display the image
        ImageIcon backgroundImage = new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\resize.jpg"); // Replace with the path to your image
        JLabel backgroundLabel = new JLabel(backgroundImage);
        backgroundLabel.setLayout(new BorderLayout());
        setContentPane(backgroundLabel);

        // Add menu items to the patient menu
        filemenu.add(edit_and_appointment);
        filemenu.add(prescribe);
        filemenu.add(Signout);

        menuBar.add(filemenu);

        // Set the JMenuBar for the frame
        setJMenuBar(menuBar);

       prescribe.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                // Open the Edit Patient form
                new Prescribe();
                dispose();
            }
        });
        Signout.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
               new Dashboard();
                dispose();
            }
        });

        edit_and_appointment.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                new EditHR();
                dispose();
            }
        });

        setVisible(true);
    }
}
mport javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.*;

public class NewPatients extends JFrame {
    private JLabel patientID = new JLabel("Patient ID: ");
    private JLabel fName = new JLabel("First Name: ");
    private JLabel lName = new JLabel("Last Name: ");
    private JLabel Email = new JLabel("Email Address: ");
    private JLabel Phone_number = new JLabel("Phone number: ");
    private JLabel MEDH = new JLabel("Medical History");
    private JLabel Addnew = new JLabel("ADD NEW PATIENTS");
    private JTextField idPatient = new JTextField();
    private JTextField firstName = new JTextField();
    private JTextField lastName = new JTextField();
    private JTextField Emailid = new JTextField();
    private JTextField Phone = new JTextField();
    JTextArea textArea = new JTextArea(400, 700);
    private JButton reg = new JButton("REGISTER");
    private JButton homebut = new JButton("Home");
    private Connection con;
    private PreparedStatement pst;

    public NewPatients() {
        setTitle("New Patients"); // Set frame title
        setLayout(null);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        setSize(width, height);
        setVisible(true);
//set label

        Addnew.setFont(new Font("Arial", Font.BOLD, 25));
        Addnew.setBounds(400, 10, 300, 25);
        Addnew.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\new-user.png"));
//
        patientID.setBounds(300, 80, 150, 25);
        patientID.setFont(new Font(null, Font.PLAIN, 16));
        idPatient.setBounds(550, 80, 150, 25);
//set label
        fName.setBounds(300, 130, 150, 25);
        fName.setFont(new Font(null, Font.PLAIN, 16));
        firstName.setBounds(550, 130, 150, 25);
//set label
        lName.setBounds(300, 180, 150, 25);
        lName.setFont(new Font(null, Font.PLAIN, 16));
        lastName.setBounds(550, 180, 150, 25);

        Email.setBounds(300, 230, 150, 25);
        Email.setFont(new Font(null, Font.PLAIN, 16));
        Emailid.setBounds(550, 230, 150, 25);
        //set phone
        Phone_number.setBounds(300, 280, 150, 25);
        Phone_number.setFont(new Font(null, Font.PLAIN, 16));
        Phone.setBounds(550, 280, 150, 25);
        //set tetxt area
        MEDH.setBounds(300, 330, 150, 25);
        MEDH.setFont(new Font(null, Font.PLAIN, 16));
        textArea.setBounds(500, 330, 200, 100);

        reg.setBounds(600, 450, 120, 30);
        reg.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\online-registration.png"));
        homebut.setBounds(600, 500, 120, 30);
        homebut.setIcon(new ImageIcon("C:\\Users\\Slindokuhle Mthalane\\OneDrive\\Desktop\\projectSFMCS\\icons\\home.png"));

        add(Addnew);
        add(patientID);
        add(fName);
        add(lName);
        add(idPatient);
        add(firstName);
        add(lastName);
        add(reg);
        add(Emailid);
        add(Email);
        add(Phone_number);
        add(Phone);
        add(MEDH);
        add(textArea);
        add(homebut);


        reg.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String id = idPatient.getText();
                String name = firstName.getText();
                String surname = lastName.getText();
                String email = Emailid.getText();
                String phones = Phone.getText();
                String text = textArea.getText();


                if (id.isEmpty() || name.isEmpty() || surname.isEmpty() || phones.isEmpty()) {
                    JOptionPane.showMessageDialog(NewPatients.this, "Please enter all fields");
                    return;
                }
                //vv
                if (!id.matches("\\d{4}")) {
                    JOptionPane.showMessageDialog(NewPatients.this, "Invalid ID format. Please enter a 4-digit ID.");
                    return;
                }

                if (!name.matches("^[A-Za-z\\s'-]+$")) {
                    JOptionPane.showMessageDialog(NewPatients.this, "Invalid First Name format.");
                    return;
                }

                if (!surname.matches("^[A-Za-z\\s'-]+$")) {
                    JOptionPane.showMessageDialog(NewPatients.this, "Invalid Last Name format.");
                    return;
                }

                if (!email.matches("^[A-Za-z0-9+_.-]+@(.+)$")) {
                    JOptionPane.showMessageDialog(NewPatients.this, "Invalid Email format.");
                    return;
                }

                if (!phones.matches("^\\d{10}$")) {
                    JOptionPane.showMessageDialog(NewPatients.this, "Invalid Phone number format (10 digits).");
                    return;
                }
                User user = addUserToDatabase(id, name, surname, email, phones,text);

                if (user != null) {
                    JOptionPane.showMessageDialog(NewPatients.this, "Registration successful for: " + user.name + " " + user.surname);


                } else {
                    JOptionPane.showMessageDialog(NewPatients.this, "Registration Failed");
                }
            }
            private User addUserToDatabase(String id, String name, String surname, String email, String phones,String text) {
                User user = null;
                try {
                    Class.forName("org.postgresql.Driver");
                    con = DriverManager.getConnection("jdbc:postgresql://localhost:5432/FMS", "postgres", "Tiny@2000");

                    //check if exist
                    PreparedStatement checkStmt = con.prepareStatement("SELECT id FROM testreg WHERE id = ?");
                    checkStmt.setString(1, id);
                    ResultSet resultSet = checkStmt.executeQuery();

                    if (resultSet.next()) {
                        JOptionPane.showMessageDialog(NewPatients.this, "User with this ID already exists.");
                    } else {
                        pst = con.prepareStatement("INSERT INTO testreg (id, name, surname, email, phones,Med_History) VALUES (?, ?, ?, ?, ?,?)");
                        pst.setString(1, id);
                        pst.setString(2, name);
                        pst.setString(3, surname);
                        pst.setString(4, email);
                        pst.setString(5, phones);
                        pst.setString(6, text);

                        int rowsAffected = pst.executeUpdate();
                        if (rowsAffected > 0) {
                            user = new User();
                            user.id = id;
                            user.name = name;
                            user.surname = surname;
                            user.email = email;
                            user.phones = phones;
                            user.Med_History = text;
                        }

                    }
                }catch (ClassNotFoundException | SQLException ex) {
                    ex.printStackTrace();
                } finally {
                    try {
                        if (pst != null) {
                            pst.close();
                        }
                        if (con != null) {
                            con.close();
                        }
                    } catch (SQLException ex) {
                        ex.printStackTrace();
                    }
                }
                return user;
            }
        });
        homebut.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                AdminHome homepage = new AdminHome();
                dispose();
            }
        });
    }
}
class User {
    String id;
    String name;
    String surname;
    String email;
    String phones;
    String Med_History;
}
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class ViewPatient {
    private JTextField idField;
    private JLabel nameLabel;
    private JLabel nameResultLabel;
    private JTextArea medHistoryTextArea;
    private JButton searchButton;
    private JButton Home;

    public ViewPatient() {
        JFrame frame = new JFrame("Database Search and Update App");
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        frame.setSize(width, height);

        JPanel panel = new JPanel();
        panel.setLayout(new FlowLayout());

        JLabel idLabel = new JLabel("Enter ID:");
        idField = new JTextField(10);
        searchButton = new JButton("Search");
        nameLabel = new JLabel("Name:");
        Home = new JButton("Home");
        nameResultLabel = new JLabel("");
        medHistoryTextArea = new JTextArea(10, 30);

        panel.add(idLabel);
        panel.add(idField);
        panel.add(searchButton);
        panel.add(Home);
        panel.add(nameLabel);
        panel.add(nameResultLabel);
        frame.add(panel, BorderLayout.NORTH);
        frame.add(new JScrollPane(medHistoryTextArea), BorderLayout.CENTER);

        searchButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                searchAndDisplayData();
            }
        });
        Home.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                AdminHome userAccounts = new AdminHome();
            }
        });
        frame.setVisible(true);
    }
    private void searchAndDisplayData() {
        String id = idField.getText().trim();

        if (id.isEmpty()) {
            JOptionPane.showMessageDialog(null, "Please enter an ID to search.");
            return;
        }
        try {
            String url = "jdbc:postgresql://localhost:5432/FMS";
            String username = "postgres";
            String password = "Tiny@2000";

            Connection conn = DriverManager.getConnection(url, username, password);

            String sql = "SELECT name, med_history FROM testreg WHERE id = ?";
            PreparedStatement preparedStatement = conn.prepareStatement(sql);
            preparedStatement.setString(1, id);

            ResultSet resultSet = preparedStatement.executeQuery();
            if (resultSet.next()) {
                String name = resultSet.getString("name");
                String medHistory = resultSet.getString("med_history");
                nameResultLabel.setText(name);
                medHistoryTextArea.setText(medHistory); // Display medical history in the JTextArea
            } else {
                nameResultLabel.setText("No record found for ID: " + id);
                medHistoryTextArea.setText(""); // Clear the JTextArea
            }
            resultSet.close();
            preparedStatement.close();
            conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Database connection error.");
        }
    }
    private void saveTextToDatabase() {
        String id = idField.getText().trim();
        String newMedHistory = medHistoryTextArea.getText();

        if (id.isEmpty()) {
            JOptionPane.showMessageDialog(null, "Please enter an ID to save to med_history.");
            return;
        }
        try {
            String url = "jdbc:postgresql://localhost:5432/FMS";
            String username = "postgres";
            String password = "Tiny@2000";

            Connection conn = DriverManager.getConnection(url, username, password);

            String updateSql = "UPDATE testreg SET med_history = ? WHERE id = ?";
            PreparedStatement updateStatement = conn.prepareStatement(updateSql);
            updateStatement.setString(1, newMedHistory);
            updateStatement.setString(2, id);

            int updatedRows = updateStatement.executeUpdate();
            if (updatedRows > 0) {
                JOptionPane.showMessageDialog(null, "Med_history updated successfully.");
            } else {
                JOptionPane.showMessageDialog(null, "No record found for ID: " + id);
            }
            updateStatement.close();
            conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Database connection error.");
        }
    }
}
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import javax.swing.table.DefaultTableModel;

public class Reports extends JFrame {
    private JButton generateReportButton;
    private JButton Home;
    private JTextField idField;
    private JTable reportTable;
    private DefaultTableModel tableModel;
    public Reports() {
        setTitle("PostgreSQL Report");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        setSize(width, height);
        setLayout(null);
        setVisible(true);
        tableModel = new DefaultTableModel();
        reportTable = new JTable(tableModel);
        JScrollPane scrollPane = new JScrollPane(reportTable);
        scrollPane.setBounds(10, 50, 780, 300);

        generateReportButton = new JButton("Generate Report");
        Home = new JButton("Home");
        generateReportButton.setBounds(10, 10, 150, 30);
        Home.setBounds(180, 10, 100, 30);
        generateReportButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {

                generateReport();
            }
        });
        Home.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                new  AdminHome();
                dispose();
            }
        });
        idField = new JTextField();
        idField.setBounds(300, 10, 300, 30);
        add(generateReportButton);
        add(idField);
        add(Home);
        add(scrollPane);
    }
    private void generateReport() {
        // Database connection details
        String url = "jdbc:postgresql://localhost:5432/FMS";
        String user = "postgres";
        String password = "Tiny@2000";

        String idList = idField.getText();
        String[] ids = idList.split(",");
        try {
            Connection connection = DriverManager.getConnection(url, user, password);
            StringBuilder query = new StringBuilder("SELECT id, med_history FROM testreg WHERE id IN (");

            for (int i = 0; i < ids.length; i++) {
                query.append("?");
                if (i < ids.length - 1) {
                    query.append(",");
                }
            }
            query.append(")");
            PreparedStatement preparedStatement = connection.prepareStatement(query.toString());

            for (int i = 0; i < ids.length; i++) {
                preparedStatement.setString(i + 1, ids[i]);
            }
            ResultSet resultSet = preparedStatement.executeQuery();

            tableModel.setRowCount(0);
            tableModel.setColumnIdentifiers(new Object[]{"id", "med_history"});
            while (resultSet.next()) {
                tableModel.addRow(new Object[]{resultSet.getString("id"), resultSet.getString("med_history")});
            }
            resultSet.close();
            preparedStatement.close();
            connection.close();
        } catch (SQLException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(this, "Error generating report: " + e.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }
    }
}

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import javax.swing.table.DefaultTableModel;

public class Reports extends JFrame {
    private JButton generateReportButton;
    private JButton Home;
    private JTextField idField;
    private JTable reportTable;
    private DefaultTableModel tableModel;
    public Reports() {
        setTitle("PostgreSQL Report");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        setSize(width, height);
        setLayout(null);
        setVisible(true);
        tableModel = new DefaultTableModel();
        reportTable = new JTable(tableModel);
        JScrollPane scrollPane = new JScrollPane(reportTable);
        scrollPane.setBounds(10, 50, 780, 300);

        generateReportButton = new JButton("Generate Report");
        Home = new JButton("Home");
        generateReportButton.setBounds(10, 10, 150, 30);
        Home.setBounds(180, 10, 100, 30);
        generateReportButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {

                generateReport();
            }
        });
        Home.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                new  AdminHome();
                dispose();
            }
        });
        idField = new JTextField();
        idField.setBounds(300, 10, 300, 30);
        add(generateReportButton);
        add(idField);
        add(Home);
        add(scrollPane);
    }
    private void generateReport() {
        // Database connection details
        String url = "jdbc:postgresql://localhost:5432/FMS";
        String user = "postgres";
        String password = "Tiny@2000";

        String idList = idField.getText();
        String[] ids = idList.split(",");
        try {
            Connection connection = DriverManager.getConnection(url, user, password);
            StringBuilder query = new StringBuilder("SELECT id, med_history FROM testreg WHERE id IN (");

            for (int i = 0; i < ids.length; i++) {
                query.append("?");
                if (i < ids.length - 1) {
                    query.append(",");
                }
            }
            query.append(")");
            PreparedStatement preparedStatement = connection.prepareStatement(query.toString());

            for (int i = 0; i < ids.length; i++) {
                preparedStatement.setString(i + 1, ids[i]);
            }
            ResultSet resultSet = preparedStatement.executeQuery();

            tableModel.setRowCount(0);
            tableModel.setColumnIdentifiers(new Object[]{"id", "med_history"});
            while (resultSet.next()) {
                tableModel.addRow(new Object[]{resultSet.getString("id"), resultSet.getString("med_history")});
            }
            resultSet.close();
            preparedStatement.close();
            connection.close();
        } catch (SQLException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(this, "Error generating report: " + e.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }
    }
}

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;
public class Prescribe extends JFrame {
    private JLabel head = new JLabel("Presciption");
    private JLabel doc_Name = new JLabel("Doctor's Name: ");
    private JLabel Patient_id = new JLabel("Patient Id: ");
    private JLabel Medicine = new JLabel("Medicine: ");
    private JLabel Diagnosis = new JLabel("Diagnosis: ");
    private JLabel Dosage = new JLabel("Dosage: ");
    private JLabel pills = new JLabel("Amount of Dosage: ");
    private JTextField Docter_name = new JTextField();
    private JTextField Patient_ID =new JTextField();
    private JTextField Medisic = new JTextField();
    private JTextField DIAGNOSIS = new JTextField();
    private JButton addprescription = new JButton("prescribe");
    private JButton Home = new JButton("Home");

    public Prescribe() {
        setTitle("New Patients"); // Set frame title
        setLayout(null);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        setSize(width, height);
        setVisible(true);

        head.setFont(new Font("Arial", Font.BOLD, 25));
        head.setBounds(500, 10, 300, 25);
        //doctors name
        doc_Name.setFont(new Font("Arial", Font.BOLD, 16));
        doc_Name.setBounds(400, 80, 300, 25);
        Docter_name.setBounds(550, 80, 150, 25);
        //patient id
        Patient_id.setFont(new Font("Arial", Font.BOLD, 16));
        Patient_id.setBounds(400, 130, 300, 25);
        Patient_ID.setBounds(550, 130, 150, 25);
//medicine
        Medicine.setFont(new Font("Arial", Font.BOLD, 16));
        Medicine.setBounds(400, 180, 300, 25);
        Medisic.setBounds(550, 180, 150, 25);
        //diagnosis
        Diagnosis.setFont(new Font("Arial", Font.BOLD, 16));
        Diagnosis.setBounds(400, 230, 300, 25);
        DIAGNOSIS.setBounds(550, 230, 150, 25);
        //dosage
        Dosage.setFont(new Font("Arial", Font.BOLD, 16));
        Dosage.setBounds(400, 280, 300, 25);
        String[] option1 = {"ones a day","twice a day","3 times a day"};
         JComboBox<String> times = new JComboBox(option1);
        String[] option2 = {"1","2","3","4","5"};
         JComboBox<String> quantity = new JComboBox(option2);
        times.setBounds(550, 280, 150, 25);
        //pilss
        pills.setFont(new Font("Arial", Font.BOLD, 16));
        pills.setBounds(400, 330, 300, 25);
        quantity.setBounds(550, 330, 150, 25);
//nutton
        addprescription.setBounds(550, 380, 150, 25);
        Home.setBounds(750, 380, 150, 25);

        add(head);
        add(doc_Name);
        add(Docter_name);
        add(Patient_id);
        add(Patient_ID);
        add(Medicine);
        add(Medisic);
        add(Diagnosis);
        add(DIAGNOSIS);
        add(Dosage);
        add(times);
        add(quantity);
        add(addprescription);
        add(Home);
        add(pills);
        addprescription.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String doctorName = Docter_name.getText();
                String patientId = Patient_ID.getText();
                String medicine = Medisic.getText();
                String diagnosis = DIAGNOSIS.getText();
                String dosageTime = (String) times.getSelectedItem();
                String dosageQuantity = (String) quantity.getSelectedItem();
                insertPrescription(doctorName, patientId, medicine, diagnosis, dosageTime, dosageQuantity);
            }
            private void insertPrescription(String doctorName, String patientId, String medicine, String diagnosis, String dosageTime, String dosageQuantity) {
                String url = "jdbc:postgresql://localhost:5432/FMS";
                String user = "postgres";
                String password = "Tiny@2000";

                try {
                    Connection connection = DriverManager.getConnection(url, user, password);

                    String sql = "INSERT INTO prescriptions (doctor_name, patient_id, medicine, diagnosis, dosage_time, dosage_quantity) VALUES (?, ?, ?, ?, ?, ?)";
                    PreparedStatement statement = connection.prepareStatement(sql);
                    statement.setString(1, doctorName);
                    statement.setString(2, patientId);
                    statement.setString(3, medicine);
                    statement.setString(4, diagnosis);
                    statement.setString(5, dosageTime);
                    statement.setString(6, dosageQuantity);

                    int rowsInserted = statement.executeUpdate();
                    if (rowsInserted > 0) {
                        JOptionPane.showMessageDialog(null, "Prescription added successfully.");
                    }
                    connection.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                    JOptionPane.showMessageDialog(null, "Error adding prescription: " + e.getMessage());
                }
            }
        });
        Home.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                HomepgDoc homepgDoc = new HomepgDoc();
                dispose();
            }
        });
    }
}

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class EditHR {
    private JTextField idField;
    private JLabel nameLabel;
    private JLabel nameResultLabel;
    private JTextArea medHistoryTextArea;
    private JButton searchButton;
    private JButton saveButton;
    private JButton Home;

    public EditHR() {
        JFrame frame = new JFrame("Database Search and Update App");
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        int width = screenSize.width;
        int height = screenSize.height - 50;
        frame.setSize(width, height);

        JPanel panel = new JPanel();
        panel.setLayout(new FlowLayout());

        JLabel idLabel = new JLabel("Enter ID:");
        idField = new JTextField(10);
        searchButton = new JButton("Search");
        saveButton = new JButton("Save to med_history");
        nameLabel = new JLabel("Name:");
        Home = new JButton("Home");
        nameResultLabel = new JLabel("");
        medHistoryTextArea = new JTextArea(10, 30);

        panel.add(idLabel);
        panel.add(idField);
        panel.add(searchButton);
        panel.add(saveButton);
        panel.add(Home);
        panel.add(nameLabel);
        panel.add(nameResultLabel);

        frame.add(panel, BorderLayout.NORTH);
        frame.add(new JScrollPane(medHistoryTextArea), BorderLayout.CENTER);
        searchButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                searchAndDisplayData();
            }
        });
        saveButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                saveTextToDatabase();
            }
        });
        Home.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                HomepgDoc userAccounts = new HomepgDoc();
            }
        });
        frame.setVisible(true);
    }
    private void searchAndDisplayData() {
        String id = idField.getText().trim();

        if (id.isEmpty()) {
            JOptionPane.showMessageDialog(null, "Please enter an ID to search.");
            return;
        }
        try {
            String url = "jdbc:postgresql://localhost:5432/FMS";
            String username = "postgres";
            String password = "Tiny@2000";

            Connection conn = DriverManager.getConnection(url, username, password);

            String sql = "SELECT name, med_history FROM testreg WHERE id = ?";
            PreparedStatement preparedStatement = conn.prepareStatement(sql);
            preparedStatement.setString(1, id);

            ResultSet resultSet = preparedStatement.executeQuery();
            if (resultSet.next()) {
                String name = resultSet.getString("name");
                String medHistory = resultSet.getString("med_history");
                nameResultLabel.setText(name);
                medHistoryTextArea.setText(medHistory); // Display medical history in the JTextArea
            } else {
                nameResultLabel.setText("No record found for ID: " + id);
                medHistoryTextArea.setText(""); // Clear the JTextArea
            }

            resultSet.close();
            preparedStatement.close();
            conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Database connection error.");
        }
    }
    private void saveTextToDatabase() {
        String id = idField.getText().trim();
        String newMedHistory = medHistoryTextArea.getText();

        if (id.isEmpty()) {
            JOptionPane.showMessageDialog(null, "Please enter an ID to save to med_history.");
            return;
        }
        try {
            String url = "jdbc:postgresql://localhost:5432/FMS";
            String username = "postgres";
            String password = "Tiny@2000";

            Connection conn = DriverManager.getConnection(url, username, password);

            String updateSql = "UPDATE testreg SET med_history = ? WHERE id = ?";
            PreparedStatement updateStatement = conn.prepareStatement(updateSql);
            updateStatement.setString(1, newMedHistory);
            updateStatement.setString(2, id);

            int updatedRows = updateStatement.executeUpdate();
            if (updatedRows > 0) {
                JOptionPane.showMessageDialog(null, "Med_history updated successfully.");
            } else {
                JOptionPane.showMessageDialog(null, "No record found for ID: " + id);
            }

            updateStatement.close();
            conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Database connection error.");
        }
    }
}

