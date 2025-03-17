# Task 1A
### proposal
#### Business context
#### Key features 
#### Technical Requirments
 - Non-Technical  
 - Technical  
#### User acceptance
- What the user wants the progamme to do
#### Ethical considerations
 - Making sure the programme meeds the legal needs and doesnt break any laws  
- This could be things such as data collection
### Software considerations
- Legal  
- Ethical  
- Social
#### Stake holders
- Employees  
- Customers  
- Legal bodies  
- Suppliers
#### Regulations/Considerations
- Intellectual property  
- Consumer protection  
- Age ratings and classifications  
- Advertising laws  
- Data protection and privacy  
- copyright and patent  
- Gambling legislation  
- Responsibilities concerning staff and empployment prctices  
- territorial restrictions  
- system security  
- equality and diversity 
#
# Task 1B
### Design
#### ERD
- Shows how evything links together
#### Use Case
- shows what people can do such as:  
- Staff amd Users  
- also this could include differnt types of staff like:  
- Admin which will have more controls than the normal staff
#### algortihms
- Flow digrams  
- Pseudo code  
- I need to add both to my design documents for technical and non - technical users  
- Also i should not make big flow diagrams and long chunks of Pseudo code  
- I should make different flow diagrams and code for differnt functions
#### DFD
- Show's how data is moved within the system
#### Data dictionaries
- Shows all variables that are going to be used in the programme
#### Data requirements
- Shows what data needs to be collected and stored and presented
#### Wire Frames
- What the programme is going to look like.  
- Make sure to explain why I have designed it the way I have
#### Database schema
- Show how data is organized in a system
#### Test stratagey
- Show how I'm going to test the programme
#
# Task 2
### Developing a prototype

#### Test
- Iterative testing  
- Test as im making  
- Final test  
- Use different data types  
- Erroneus, Normal and extreme
#### Document
- Document the making process  
- Testing
#### 2+ Laungages
- My choices:  
- C#, SQL
#### acessability
- Make sure it is usable fore evryone/target audience  
- Make sure it is easy to navigate
#### GDPR
- Make sure it follows legal and ethical considerations  
#
# Task 3A
### User Feedback
#### FeedBack plan
- What people are going to as about my prototype  
- Introduction  
- Wasy to collect data  
- Form questions  
- Interview questions
#### Google forms
- Open ended questions  
- Ask about functionality  
- Ask about navigation
#### Interviews
- Interview people on my prototype
#### recording of prototype
- Recording of me using the prototype to show people im going to interview
#### Report
- Introduction  
- Data methodoligy  
- Findings  
- Conclusion
#### Graphs
- From google forms
#### Non-Technical audience
- People to see if they can use the programme easily and smoothly
#### technical audience
- People to see if all the functions work properly
#
# Task 3B
### Evaluation
- Evauate on the feedback gathered  
- Explain if any improvments can be made to the prototype
#
# Code
### sql connection
```C#
string ConnectionString = "Data Source=(LocalDB)\\MSSQLLocalDB;AttachDbFilename=\"C:\\Users\\billy\\OneDrive - Middlesbrough College\\C#\\SimpleWeatherApiExample\\SimpleWeatherApi\\SaveDB.mdf\";Integrated Security=True;Connect Timeout=30";

SqlConnection sqlConnection = new SqlConnection(ConnectionString);
SqlCommand command = new SqlCommand("SaveForecast", sqlConnection);
command.CommandType = CommandType.StoredProcedure;
```
### API connection
```C#
private const string API_KEY = "b1fe4659e300363e368f4ce2cf007fac";
location = txtCity.Text;
WebClient client = new WebClient();
string ForecastUrl =
"http://api.openweathermap.org/data/2.5/forecast?" +
"q=" + location + "&mode=xml&units=metric&APPID=" + API_KEY;
txtCity.Clear();
DisplayForecast(client.DownloadString(ForecastUrl));
```

### Output API data
```C#
DataTable dt = new DataTable();

XmlDocument xmlDoc = new XmlDocument();
xmlDoc.LoadXml(xml);

XmlNode locNode = xmlDoc.SelectSingleNode("weatherdata/location");
txtCity.Text = locNode.SelectSingleNode("name").InnerText;
          
dt.Columns.Add("Day");
dt.Columns.Add("Time");
dt.Columns.Add("Wind");
dt.Columns.Add("Rain");
dt.Columns.Add("Temperature");

foreach (XmlNode timeNode in xmlDoc.SelectNodes("//time"))
{
    DateTime time =
        DateTime.Parse(timeNode.Attributes["from"].Value);

    XmlNode windNode = timeNode.SelectSingleNode("windSpeed");
    string wind = windNode.Attributes["mps"].Value;

    XmlNode TempNode = timeNode.SelectSingleNode("temperature");
    string Temp = TempNode.Attributes["value"].Value;

    XmlNode rainNode = timeNode.SelectSingleNode("precipitation");
    string rain = rainNode.Attributes["probability"].Value;

    dt.Rows.Add(time.DayOfWeek.ToString(), time.ToShortTimeString(), wind.ToString() + "m/s", rain.ToString() + "%", Temp.ToString() + "°C");

    dataGridView1.DataSource = dt;

```
### Data Table

```C#
string connectionString = "Data Source=(LocalDB)\\MSSQLLocalDB;AttachDbFilename=\"C:\\M2301290\\billy\\OneDrive - Middlesbrough College\\C#\\Hospital\\HospitalDB.mdf\";Integrated Security=True;Connect Timeout=30";

SqlConnection sqlConnection = new SqlConnection(connectionString);


SqlCommand cmd = new SqlCommand("GetPatientDetails", sqlConnection);

cmd.CommandType = CommandType.StoredProcedure;

SqlDataAdapter sd = new SqlDataAdapter(cmd);

DataTable dt = new DataTable();

sqlConnection.Open();

sd.Fill(dt);

sqlConnection.Close();

//Read rows of database and extract fields


foreach (DataRow dr in dt.Rows)

{

    int personId = (int)(dr["Id"]);

    string personFirstName = (string)(dr["FirstName"]);

    string personLastName = (string)(dr["LastName"]);

    string personDOB = (string)(dr["DOB"]);

    string PersonNumber = (string)(dr["Number"]);

    string PersonAddress = (string)(dr["Address"]);

    string PersonEmail = (string)(dr["Email"]);

    string personDoctor = (string)(dr["Doctor"]);

    txtPatients.AppendText(personId + "\t" + personFirstName + "\t" + personLastName + "\t" + personDOB + "\t" + PersonNumber.ToString() + "\t" + PersonAddress + "\t" + PersonEmail + "\t" + personDoctor + Environment.NewLine);
}

```
#
# Checklist
### Task 1
#### Proposal
- Proposal Overview  
  - outline Digital solution
  - Key objectives
- Key requirments of the breif
  - Interactive teaching and learning resources
  - Encouragemebt of wider learning
  - support for assessment and monitoring
  - collaborative tools for teaching and learning
  - accessibilty features for a diverse user base
  - A reward system for learning
  - elements of gamified learning
- Data handling
  - Managing appointments or booking (if applicable)
  - Storing and using data for customised solutions
  - supporting digital contents delivery across various platforms/devices
  - catering to different strategies for learning through diverse content
  - Implementing gamified learning approaches
  - Providing accessibility features
  - Incorporating social learning through integration with social media APIs or developing a website that utilises a back-end database.
- Risk Management
  - Malicious or inappropriate use
  - Data breaches
  - Cross-site scripting
  - SQL injection
- Wider issues
  - General issues such as privacy and potential user errors
  - Specific issues relevant to your scenario
  - Technical issues and guidlines that are relevant to software development and industrial context
  - Laws, legislations & regulations that need to be adhered to
- Current practices and emerging technology
  - Apps and mobile devices
  - Video or remote instruction
  - Use of AR/VR technologies
- Functional and Non-functional requirments
  - Functional requirments
  - Non-functional requirments
  - KPI
  - User acceptance criteria

#### Design
- Visual/Interface Designs
- Data requirments
- Algorithms
- Test stratagey
- Use case
- DFD
- ERD
### Task 2
#### Code
- 2 laungages
- Iterative Testing
- Documentation
  - Testing
  - Assets
### Task 3a
#### Gathering feedback
- Google forms
- interviews
- Report
- Feedback plan
### Task 3b
#### Evaluation  
  
  

![image](https://github.com/user-attachments/assets/d792b82d-6e32-4deb-a20f-b28dbfd83fed)

![image](https://github.com/user-attachments/assets/f0775c7b-ecee-4705-8c2a-dd049a6d2000)

![{667D95EB-B0B8-4933-B941-053F3A3E12F1}](https://github.com/user-attachments/assets/0618d2e8-09e5-4d2a-b56d-caad7db8330c)

![{2A3BE2CB-F106-459B-88E3-12969EAE99F7}](https://github.com/user-attachments/assets/11b7313a-6cbc-48b7-9ffb-9be9e43be45d)

![{A9AABED7-46D5-4854-9CD0-DB71431BD8BD}](https://github.com/user-attachments/assets/7ce1295c-51e9-45a4-a637-5988d7ce33e0)

![image](https://github.com/user-attachments/assets/de6333a8-bea2-4123-a238-588fc4a02e45)

![image](https://github.com/user-attachments/assets/fe9180dd-09fa-4540-888c-3e5105a41519)









