# Challenge-Back-End
Prueba de Back-End a nivel junior
Here you can found a challenge for junior back-end and the amswers with a simple example code 

1. You're building a high-throughput API for a cryptocurrency trading
platform. For this platform, time is extremely important because
microseconds count when processing high-volume trade orders. For
communicating with the API, you want to choose the verb that is fastest
for read-only operations.
What verb should you choose for retrieving trade orders with the API
server?
SELECT ONLY ONE
1. GET
2. UPDATE
3. DELETE
4. POST

5. ANSWER:  GET
## EXAMPLE CODE
   fetch('/trade_orders', { method: 'GET' })
  .then(response => response.json())
  .then(data => console.log(data));
   
2. You work for a Customer Relationship Management (CRM) company. The
company's clients gain CRM access through a RESTful API. The CRM allows
clients to add contact information for customers, prospects, and related persons
(e.g., virtual assistants or marketing directors). You want to choose an appropriate API request path so clients can easily retrieve information for a
single contact while also being flexible for future software changes.
Which of the following API paths should you use?
SELECT ONLY ONE
1. /customers/{customer_id}
2. /contacts/{contact_id}
3. /contacts/{contact_type}/all
4. /customers/all
5. ANSWER: /contacts/{contact_id}
   
  ## EXAMPLE CODE
   fetch(`/contacts/${contactid}`, { method: 'GET' })
  .then(response => response.json())
  .then(data => console.log(data));
   
3. You work for a large social media network, and you've been tasked witherror
handling for the API. You're trying to decide on an appropriate errorcode for
authentication failures based on non-existent users and incorrect passwords. You
want to balance security against brute force attacks with providing descriptive
and true error codes.
Which HTTP error code(s) should you use to keep the system secure and still report
that an error occurred?
SELECT ONLY ONE
1. 404 if the user doesn't exist, and 403 if the password is wrong.
2. 403 if the user doesn't exist, and 401 if the password is wrong.
3. 500 if the user doesn't exist or if the password is wrong.
4. 401 if the user doesn't exist or if the password is wrong.
  5. ANSWER: 404 if the user doesn´t exisy, and 403 if the password is worng.
  ## EXAMPLE CODE:
  async function loginUser(username, password) {
  try {
    const response = await fetch('/login', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ username, password })
    });
    if (!response.ok) {
      throw new Error(response.status === 401 ? 'Unauthorized' : 'Login failed');
    }
    const data = await response.json();
    console.log('Login successful:', data.token);
    } catch (error) {
    console.error('Error:', error.message);
  }
}
     // Ejemplo de uso
    loginUser('user123', 'password123');

4. You're writing documentation for requesting information about a given user in
your system. Your system uses UUIDS (universally unique identifiers) as user
identifiers. In your documentation, you want to show an example.
True or false: You should put a fake UUID into the example code (instead of just the
text "UUID") as a placeholder.
SELECT ONLY ONE
1. TRUE
2. FALSE
3.ANSWER: TRUE

##EXAMPLE CODE 
const fakeUUID = '123e4567-e89b-12d3-a456-426614174000';

async function getUserData(uuid) {
  try {
    const response = await fetch(`/api/users/${uuid}`, {
      method: 'GET',
    });
    if (!response.ok) {
      throw new Error(`Error ${response.status}: Unable to fetch user data`);
    }
    const data = await response.json();
    console.log('User data:', data);
  } catch (error) {
    console.error('Error fetching user data:', error.message);
  }
}
getUserData(fakeUUID);

5. You're building code to handle errors issued from a remote API server. The
response may or may not have an error.
How much work should your method, handleErrors(response),
handle?
SELECT ONLY ONE
1. Check for the presence of an error. If it exists, then set a class property to the
error.
2. Check for the presence of an error. If it exists, throw an exception with the error.

3. Check for the presence of an error. If it exists, set a class property to the error,
then throw an exception.

4. ANSWER: Check for the presence of an error. If it exists, set a class property to the error,
then throw an exception.

##EXAMPLE CODE:
function handleErrors(response) {
  if (response.error) {
    throw new Error(response.error);
  }
  return response.data;
}

6. You have two classes: a database driver and an email driver. Both classes need
to set errors so that your front-end interface displays any errors that transpire on
your platform.
Which way should you implement this error handling?
SELECT ONLY ONE
1. Write the error handling the same way in both classes, but keep it to one line of
code.
2. Make a trait to handle errors so it'll collect errors in any class that uses it.
3. Make a driver-based error provider to handle errors in all classes that can issue
errors.
4. ANSWER:  Make a trait to handle errors so it'll collect errors in any class that uses it.
##EXAMPLE CODE:
// Manejador de errores simple
const errorHandler = {
  errors: [],
  log(error) {
    this.errors.push(error);
    console.error(`Error: ${error}`);
  }
};

// Clase de base de datos con manejo de errores
class Database {
  connect() {
    errorHandler.log('Failed to connect to the database');
  }
}

// Clase de email con manejo de errores
class Email {
  send() {
    errorHandler.log('Failed to send email');
  }
}

// Uso
const db = new Database();
db.connect();

const email = new Email();
email.send();

console.log('Errores:', errorHandler.errors);

7. You need to name the private method in your class that handles loopingthrough
eCommerce products to collect and parse data. That data gets stored in an array
and set as a class property.
Which of the following should you use to name your method?
SELECT ONLY ONE
1. loopThroughProductsAndParseData()
2. loopProductsAndParse()
3. parseDataForProducts()
4. parseDataForProductsAndSetArray()
5. ANSWER: parseDataForProducts()
   ##EXAMPLE CODE
   class ProductParser {
  constructor() {
    this.productData = [];
  }

  loopThroughProductsAndParseData() {
    this.products.forEach(product => {
      this.productData.push(this.parseProductData(product));
    });
  }

  parseProductData(product) {
  }
}
8. There are multiple places in your codebase that need to access the
database. To access the database, you need to supply credentials. You
want to balance security with useability.
What strategy should you use to store and access these credentials?
SELECT ONLY ONE
1. Put them in the code that connects to the database for each place that needs
database access.
2. Put them in a configuration file, then include that file in the code everywhere
that needs to access the database.
3. Put the credentials into a configuration file, then load them with a database
service provider.
4. Put them in a .env file, load data from it into a configuration system, then
request the credentials from a database service provider.

5. ANSWER: Put them in a .env file, load data from it into a configuration system, then
request the credentials from a database service provider.
##EXAMPLE CODE

// .env file
DB_HOST=localhost
DB_USERNAME=myuser
DB_PASSWORD=mypassword

const config = {
  database: {
    host: process.env.DB_HOST,
    username: process.env.DB_USERNAME,
    password: process.env.DB_PASSWORD,
  },
};

// Simulation of a database client (replace this with the real client)
const mockDatabaseClient = {
  connect: async () => console.log('Conexión establecida'),
};

// Database service provider
class DatabaseServiceProvider {
  async getConnection() {
    const { host, username, password } = config.database;
    try {
      await mockDatabaseClient.connect();
      console.log(`Connected to database on ${host} with user ${username}`);
    } catch (error) {
      console.error('Error connecting to database:', error);
      throw new Error('Could not establish database connection');
    }
  }
}

// Example of use
(async () => {
  const dbService = new DatabaseServiceProvider();
  try {
    await dbService.getConnection();
  } catch (error) {
    console.error('Connection failed:', error);
  }
})();

