
# Movie Ticket Booking System

## README

### System Architecture

The Movie Ticket Booking System is designed to simplify the booking process for users. It follows a client-server architecture where the client is a Java-based graphical user interface (GUI) and the server is a MySQL database that stores user information and booking data. The major components of the system include:

- **User Interface**: A Java Swing GUI that allows users to interact with the system.
- **Database**: A MySQL database that stores user details, movie information, and theater schedules.
- **Controllers**: Java classes that handle user inputs, interactions with the database, and manage the flow of the application.

The user flow is as follows:
1. Users can register or login to the system.
2. They can choose a movie, theater, date, and showtime, along with the number of tickets.
3. The system calculates the booking cost and displays a summary.
4. Finally, a receipt is generated for completed transactions.

### Core Components and Modules

Below are the core components of the system:

#### 1. **Login.java**
Handles user authentication when registering or logging into the system. 

**Key Method:**
```java
public void workWithDatabase()
```
This method retrieves user credentials from the database and checks for valid combinations to allow user access.

#### 2. **Register.java**
Manages new user registrations into the system.

**Key Method:**
```java
private void jButton1ActionPerformed(java.awt.event.ActionEvent evt)
```
This action method retrieves input data for the new user and stores it in the database.

#### 3. **Movie.java**
Allows users to select a movie, theater, date, and showtime.

**Key Method:**
```java
public void workWithDatabase()
```
This method inserts selected movie details into the system and retrieves available tickets.

#### 4. **Payment.java**
Handles the payment process after the user confirms their booking.

**Key Method:**
```java
private void jButton1ActionPerformed(java.awt.event.ActionEvent evt)
```
This method processes the payment information and transitions the user to the receipt display.

#### 5. **Receipt.java**
Displays the booking summary and details after a successful transaction.

**Key Method:**
```java
public recepit(String p1,String p2,String p3,String p4,int p5,String p6)
```
This constructor initializes the receipt with the booking details provided by the user.

### Example Code Snippets

Here's an example of how a user registers using `Register.java`:

```java
private void jButton1ActionPerformed(java.awt.event.ActionEvent evt) {
    String name = jTextField1.getText();
    String email = jTextField2.getText();
    String password = jTextField3.getText();

    if (name.isEmpty() || email.isEmpty() || password.isEmpty()) {
        JOptionPane.showMessageDialog(this, "Please enter valid details");
    } else {
        try {
            Statement s = conn.createStatement();
            String query = "insert into register values('" + name + "','" + email + "','" + password + "');";
            s.executeUpdate(query);
            this.setVisible(false); // Hide registration form
            new login().setVisible(true); // Show login form
        } catch (SQLException e) {
            Logger.getLogger(register.class.getName()).log(Level.SEVERE, null, e);
        }
    }
}
```

### How to Run the Project

1. Ensure that you have the Java Development Kit (JDK) installed.
2. Download and install MySQL and set up your database. Import the provided schema.
3. Open the project using NetBeans.
4. Execute the main class that contains your user interface (usually `login` class).

### Technologies Used

- **Frontend**: Java Swing for building the GUI.
- **Database**: MySQL for storing user and booking data.
- **IDE**: NetBeans 8.2

