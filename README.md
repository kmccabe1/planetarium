# Use Case
- **ID**: 1
- **Name**: User Registration
- **Description**: Users should be able to open a new User account with the Planetarium
- **System**: Planetarium Application
- **Preconditions**:
    - No registered user with username "Yelan Burst Depth-Clarion Dice"
    - Registered user with username "Yelan"
- **Actors**:
    - User
    - Planetarium Application
***
- **ID**: 2
- **Name**: User Login
- **Description**: Users should be able to securely access their account
- **System**: Planetarium Application
- **Preconditions**:
    - User account with valid username and valid password from [Test Data](#test-data) created
- **Actors**:
    - User
    - Planetarium Application
***
- **ID**: 3
- **Name**: View Planets/Moons
- **Description**: Users should be able to see planets and moons added to the Planetarium
- **System**: Planetarium Application
- **Preconditions**:
    - User is logged in
- **Actors**:
    - User
    - Planetarium Application
***
- **ID**: 4
- **Name**: Add New Planet
- **Description**: Users should be able to add new Planets to the Planetarium
- **System**: Planetarium Application
- **Preconditions**:
    - User is logged in
    - No planet with name "UmbrabilisOrchisExquisiteThrow"
- **Actors**:
    - User
    - Planetarium Application
***
- **ID**: 5
- **Name**: Remove Planet
- **Description**: Users should be able to remove Planets from the Planetarium
- **System**: Planetarium Application
- **Preconditions**:
    - User is logged in
    - Planet with name "UmbrabilisOrchisExquisiteThrow" exists
- **Actors**:
    - User
    - Planetarium Application
***
- **ID**: 6
- **Name**: Add Moon
- **Description**: Users should be able to add Moons to the Planetarium associated with a Planet
- **System**: Planetarium Application
- **Preconditions**:
    - User is logged in
    - Planet with name "UmbrabilisOrchisExquisiteThrow" exists
    - No moon with name "" exists
- **Actors**:
    - User
    - Planetarium Application
***
- **ID**: 7
- **Name**: Remove Moon
- **Description**: Users should be able to remove Moons from the Planetarium
- **System**: Planetarium Application
- **Preconditions**:
    - User is logged in
    - Planet with name "UmbrabilisOrchisExquisiteThrow" exists
    - Moon with name "" exists
- **Actors**:
    - User
    - Planetarium Application

# Test Data
**Positive**:
- valid username = "Yelan Burst Depth-Clarion Dice"
- valid password = "Turn Control Adapt With Ease!!"
- valid planet name = "UmbrabilisOrchisExquisiteThrow"
- valid moon name = "Imperatrix Umbrosa Wishbearer!"
- existing username = "Yelan"
- valid planet id = "1"
- existing planet name = "Furina"
- existing moon name = "Fischl"

**Negative**:
- non-unique username = "Yelan"
- non-existing username = "Raiden"
- correct password = "Aqua Simulacra"
- wrong password = "Lingering Lifeline"
- too long username = "Beware the Trickster's Dice!!!!"
- too long password = "Necessary Calculation Passive!!"
- non-unique planet name = "Furina"
- too long planet name = "Bait-and-Switch Dealer'sSleight"
- too long moon name = "Secret Art: Musou Shinsetsu!!!!"
- non-unique moon name = "Fischl"
- invalid planet id = "99"
- non-existing planet name = "Beidou"
- non-existing moon name = "Layla"

## Decision Tables
### User Registration
<table>
    <tr>
        <th>Scenario</th><th>Username</th><th>Password</th><th>Result</th>
    </tr>
    <tr>
        <td>Positive Scenario</td><td>valid username</td><td>valid password</td><td>user registered</td>
    </tr>
    <tr>
        <td>Negative Scenario Username not unique</td><td>non-unique username</td><td>valid password</td><td>user not registered</td>
    </tr>
    <tr>
        <td>Negative Scenario Username too long</td><td>too long username</td><td>valid password</td><td>user not registered</td>
    </tr>
    <tr>
        <td>Negative Scenario Password too long</td><td>valid username</td><td>too long password</td><td>user not registered</td>
    </tr>
    <tr>
        <td>Negative Scenario credentials too long</td><td>too long username</td><td>too long password</td><td>user not registered</td>
    </tr>
    <tr>
        <td>Negative Scenario username taken and password too long</td><td>non-unique username</td><td>too long password</td><td>user not registered</td>
    </tr>
</table>

### User Login
<table>
    <tr>
        <th>Scenario</th><th>Username</th><th>Password</th><th>Result</th>
    </tr>
    <tr>
        <td>Positive Scenario</td><td>registered username</td><td>correct password</td><td>user logged in</td>
    </tr>
    <tr>
        <td>Negative Scenario Username not registered</td><td>not registered username</td><td>valid password</td><td>user not logged in</td>
    </tr>
    <tr>
        <td>Negative Scenario Password incorrect</td><td>registered username</td><td>wrong password</td><td>user not logged in</td>
    </tr>
</table>

### Add New Planet
<table>
    <tr>
        <th>Scenario</th><th>Planet name</th><th>Image</th><th>Result</th>
    </tr>
    <tr>
        <td>Positive Scenario</td><td>valid planet name</td><td>N/A</td><td>planet added "owned" by user</td>
    </tr>
    <tr>
        <td>Positive Scenario</td><td>valid planet name</td><td>valid image</td><td>planet added with image and "owned" by user</td>
    </tr>
    <tr>
        <td>Negative Scenario Planet name not unique and no image</td><td>non-unique planet name</td><td>N/A</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Planet name not unique and valid image</td><td>non-unique planet name</td><td>valid image</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Planet name too long and no image</td><td>too long planet name</td><td>N/A</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Planet name too long and valid image</td><td>too long planet name</td><td>valid image</td><td>planet not added</td>
    </tr>
</table>

### Add New Moon
<table>
    <tr>
        <th>Scenario</th><th>Moon name</th><th>Planet ID</th><th>Image</th><th>Result</th>
    </tr>
    <tr>
        <td>Positive Scenario</td><td>valid moon name</td><td>valid planet id</td><td>N/A</td><td>moon added "owned" by planet id</td>
    </tr>
    <tr>
        <td>Positive Scenario</td><td>valid moon name</td><td>valid planet id</td><td>valid image</td><td>moon added with image "owned" by planet id</td>
    </tr>
    <tr>
        <td>Negative Scenario Moon name not unique and no image</td><td>non-unique moon name</td><td>valid planet id</td><td>N/A</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Moon name not unique and valid image</td><td>non-unique moon name</td><td>valid planet id</td><td>valid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Moon name too long and no image</td><td>too long moon name</td><td>valid planet id</td><td>N/A</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Moon name too long and valid image</td><td>too long moon name</td><td>valid planet id</td><td>valid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Planet ID invalid and no image</td><td>valid moon name</td><td>invalid planet id</td><td>N/A</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Planet ID invalid and valid image</td><td>valid moon name</td><td>invalid planet id</td><td>valid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Moon name too long, invalid planet id, and no image</td><td>too long moon name</td><td>invalid planet id</td><td>N/A</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Moon name too long, invalid planet id, and valid image</td><td>too long moon name</td><td>invalid planet id</td><td>valid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Moon name not unique, invalid planet id, and no image</td><td>non-unique moon name</td><td>invalid planet id</td><td>N/A</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Scenario Moon name not unique, invalid planet id, and valid image</td><td>non-unique moon name</td><td>invalid planet id</td><td>valid image</td><td>moon not added</td>
    </tr>
</table>

### Delete Planet
<table>
    <tr>
        <th>Scenario</th><th>Planet Name</th><th>Result</th>
    </tr>
    <tr>
        <td>Positive Scenario</td><td>existing planet name</td><td>planet deleted</td>
    </tr>
    <tr>
        <td>Negative Scenario</td><td>non-existing planet name</td><td>planet failed to delete</td>
    </tr>
</table>

### Delete Moon
<table>
    <tr>
        <th>Scenario</th><th>Moon Name</th><th>Result</th>
    </tr>
    <tr>
        <td>Positive Scenario</td><td>existing moon name</td><td>moon deleted</td>
    </tr>
    <tr>
        <td>Negative Scenario</td><td>non-existing moon name</td><td>moon failed to delete</td>
    </tr>
</table>

### View Planets/Moons
<table>
    <tr>
        <th>Scenario</th><th>View Planet</th><th>View Moon</th><th>Planet Added</th><th>Moon Added</th><th>Result</th>
    </tr>
    <tr>
        <td>Positive Scenario View Planet added</td><td>Yes</td><td>N/A</td><td>Yes</td><td>N/A</td><td>User can view the planet successfully added</td>
    </tr>
    <tr>
        <td>Positive Scenario View Moon added</td><td>N/A</td><td>Yes</td><td>N/A</td><td>No</td><td>User can view the moon successfully added</td>
    </tr>
</table>

# Test Cases
<table>
    <tr>
        <th>Test Case ID</th>
        <th>Description</th>
        <th>Preconditions</th>
        <th>Test Data</th>
        <th>Steps</th>
        <th>Expected Outcome</th>
        <th>Actual Outcome</th>
        <th>Tester</th>
        <th>Status</th>
    </tr>
    <tr>
        <td>1</td>
        <td>Given a valid username and password a user should be able to register with the Planetarium</td>
        <td>No registered user with username "Yelan Burst Depth-Clarion Dice"</td>
        <td>valid username, valid password</td>
        <td>
            <ol>
                <li>Get to landing page</li>
                <li>Pick option to create account</li>
                <li>Provide valid username</li>
                <li>Provide valid password</li>
                <li>Select create to register account</li>
            </ol>
        </td>
        <td>User should be registered with the planetarium application</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>2</td>
        <td>Given a non-unique username and valid password a user should not be able to register an account</td>
        <td>Registered user with username "Yelan"</td>
        <td>non-unique username, valid password</td>
        <td>
            <ol>
                <li>Get to landing page</li>
                <li>Pick option to create account</li>
                <li>Provide non-unique username</li>
                <li>Provide valid password</li>
                <li>User should be informed account creation failed</li>
            </ol>
        </td>
        <td>User not registered</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>3</td>
        <td>Given a too long username and valid password a user should not be able to register an account</td>
        <td>N/A</td>
        <td>too long username, valid password</td>
        <td>
            <ol>
                <li>Get to landing page</li>
                <li>Pick option to create account</li>
                <li>Provide too long username</li>
                <li>Provide valid password</li>
                <li>User should be informed account creation failed</li>
            </ol>
        </td>
        <td>User not registered</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>4</td>
        <td>Given a valid username and too long password a user should not be able to register an account</td>
        <td>N/A</td>
        <td>valid username, too long password</td>
        <td>
            <ol>
                <li>Get to landing page</li>
                <li>Pick option to create account</li>
                <li>Provide valid username</li>
                <li>Provide too long password</li>
                <li>User should be informed account creation failed</li>
            </ol>
        </td>
        <td>User not registered</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>5</td>
        <td>Given a too long username and too long password a user should not be able to register an account</td>
        <td>N/A</td>
        <td>too long username, too long password</td>
        <td>
            <ol>
                <li>Get to landing page</li>
                <li>Pick option to create account</li>
                <li>Provide too long username</li>
                <li>Provide too long password</li>
                <li>User should be informed account creation failed</li>
            </ol>
        </td>
        <td>User not registered</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>6</td>
        <td>Given a non-unique username and too long password a user should not be able to register an account</td>
        <td>Registered user with username "Yelan"</td>
        <td>non-unique username, too long password</td>
        <td>
            <ol>
                <li>Get to landing page</li>
                <li>Pick option to create account</li>
                <li>Provide non-unique username</li>
                <li>Provide too long password</li>
                <li>User should be informed account creation failed</li>
            </ol>
        </td>
        <td>User not registered</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>7</td>
        <td>Given an existing username and correct password a user should be able to login</td>
        <td>Registered user with username "Yelan"</td>
        <td>existing username, correct password</td>
        <td>
            <ol>
                <li>Get to landing page</li>
                <li>Provide existing username</li>
                <li>Provide correct password</li>
                <li>User should be logged in</li>
            </ol>
        </td>
        <td>User logged in</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>8</td>
        <td>Given an non-existing username and valid password a user should not be able to login</td>
        <td>N/A</td>
        <td>non-existing username, valid password</td>
        <td>
            <ol>
                <li>Get to landing page</li>
                <li>Provide non-existing username</li>
                <li>Provide valid password</li>
                <li>User should be informed login attempt failed</li>
            </ol>
        </td>
        <td>User failed to login</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>9</td>
        <td>Given an existing username and wrong password a user should not be able to login</td>
        <td>Registered user with username "Yelan"</td>
        <td>existing username, wrong password</td>
        <td>
            <ol>
                <li>Get to landing page</li>
                <li>Provide existing username</li>
                <li>Provide wrong password</li>
                <li>User should be informed login attempt failed</li>
            </ol>
        </td>
        <td>User failed to login</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>10</td>
        <td>Given a valid planet name and no image a user should be able to add the planet to planetarium</td>
        <td>No planet with name "UmbrabilisOrchisExquisiteThrow"</td>
        <td>valid planet name, no image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide valid planet name</li>
                <li>Provide no image</li>
                <li>Planet should be added to planetarium</li>
            </ol>
        </td>
        <td>Planet added to planetarium with no image and "owned" by user</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>11</td>
        <td>Given a valid planet name and valid image a user should be able to add the planet to planetarium</td>
        <td>No planet with name "UmbrabilisOrchisExquisiteThrow"</td>
        <td>valid planet name, valid image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide valid planet name</li>
                <li>Provide valid image</li>
                <li>Planet should be added to planetarium with image</li>
            </ol>
        </td>
        <td>Planet added to planetarium with provided image and "owned" by user</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>12</td>
        <td>Given a non-unique planet name and no image a user should not be able to add the planet to planetarium</td>
        <td>N/A</td>
        <td>non-unique planet name, no image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide non-unique planet name</li>
                <li>Provide no image</li>
                <li>User should be informed planet was not added to planetarium</li>
            </ol>
        </td>
        <td>Planet not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>13</td>
        <td>Given a non-unique planet name and valid image a user should not be able to add the planet to planetarium</td>
        <td>N/A</td>
        <td>non-unique planet name, valid image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide non-unique planet name</li>
                <li>Provide valid image</li>
                <li>User should be informed planet was not added to planetarium</li>
            </ol>
        </td>
        <td>Planet not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>14</td>
        <td>Given a too long planet name and no image a user should not be able to add the planet to planetarium</td>
        <td>N/A</td>
        <td>too long planet name, no image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide too long planet name</li>
                <li>Provide no image</li>
                <li>User should be informed planet was not added to planetarium</li>
            </ol>
        </td>
        <td>Planet not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>15</td>
        <td>Given a too long planet name and valid image a user should not be able to add the planet to planetarium</td>
        <td>N/A</td>
        <td>too long planet name, valid image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide too long planet name</li>
                <li>Provide valid image</li>
                <li>User should be informed planet was not added to planetarium</li>
            </ol>
        </td>
        <td>Planet not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>16</td>
        <td>Given a valid moon name, valid planet id, and no image a user should be able to add the moon to planetarium</td>
        <td>No moon with name "Imperatrix Umbrosa Wishbearer!"</td>
        <td>valid moon name, valid planet id, no image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide valid moon name</li>
                <li>Provide valid planet id</li>
                <li>Provide no image</li>
                <li>User should be informed moon was added to planetarium</li>
            </ol>
        </td>
        <td>Moon added to planetarium "owned" by planet id</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>17</td>
        <td>Given a valid moon name, valid planet id, and valid image a user should be able to add the moon to planetarium</td>
        <td>No moon with name "Imperatrix Umbrosa Wishbearer!"</td>
        <td>valid moon name, valid planet id, valid image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide valid moon name</li>
                <li>Provide valid planet id</li>
                <li>Provide valid image</li>
                <li>User should be informed moon was added to planetarium</li>
            </ol>
        </td>
        <td>Moon added with image to planetarium "owned" by planet id</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>18</td>
        <td>Given a non-unique moon name, valid planet id, and no image a user should not be able to add the moon to planetarium</td>
        <td>N/A</td>
        <td>non-unique moon name, valid planet id, no image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide non-unique moon name</li>
                <li>Provide valid planet id</li>
                <li>Provide no image</li>
                <li>User should be informed moon was not added to planetarium</li>
            </ol>
        </td>
        <td>Moon not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>19</td>
        <td>Given a non-unique moon name, valid planet id, and valid image a user should not be able to add the moon to planetarium</td>
        <td>N/A</td>
        <td>non-unique moon name, valid planet id, valid image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide non-unique moon name</li>
                <li>Provide valid planet id</li>
                <li>Provide valid image</li>
                <li>User should be informed moon was not added to planetarium</li>
            </ol>
        </td>
        <td>Moon not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>20</td>
        <td>Given a too long moon name, valid planet id, and no image a user should not be able to add the moon to planetarium</td>
        <td>N/A</td>
        <td>too long moon name, valid planet id, no image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide too long moon name</li>
                <li>Provide valid planet id</li>
                <li>Provide no image</li>
                <li>User should be informed moon was not added to planetarium</li>
            </ol>
        </td>
        <td>Moon not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>21</td>
        <td>Given a too long moon name, valid planet id, and valid image a user should not be able to add the moon to planetarium</td>
        <td>N/A</td>
        <td>too long moon name, valid planet id, valid image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide too long moon name</li>
                <li>Provide valid planet id</li>
                <li>Provide valid image</li>
                <li>User should be informed moon was not added to planetarium</li>
            </ol>
        </td>
        <td>Moon not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>22</td>
        <td>Given a valid moon name, invalid planet id, and no image a user should not be able to add the moon to planetarium</td>
        <td>N/A</td>
        <td>valid moon name, invalid planet id, no image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide valid moon name</li>
                <li>Provide invalid planet id</li>
                <li>Provide no image</li>
                <li>User should be informed moon was not added to planetarium</li>
            </ol>
        </td>
        <td>Moon not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>23</td>
        <td>Given a valid moon name, invalid planet id, and valid image a user should not be able to add the moon to planetarium</td>
        <td>N/A</td>
        <td>valid moon name, invalid planet id, valid image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide valid moon name</li>
                <li>Provide invalid planet id</li>
                <li>Provide valid image</li>
                <li>User should be informed moon was not added to planetarium</li>
            </ol>
        </td>
        <td>Moon not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>24</td>
        <td>Given a too long moon name, invalid planet id, and no image a user should not be able to add the moon to planetarium</td>
        <td>N/A</td>
        <td>too long moon name, invalid planet id, no image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide too long moon name</li>
                <li>Provide invalid planet id</li>
                <li>Provide no image</li>
                <li>User should be informed moon was not added to planetarium</li>
            </ol>
        </td>
        <td>Moon not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>25</td>
        <td>Given a too long moon name, invalid planet id, and valid image a user should not be able to add the moon to planetarium</td>
        <td>N/A</td>
        <td>too long moon name, invalid planet id, valid image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide too long moon name</li>
                <li>Provide invalid planet id</li>
                <li>Provide valid image</li>
                <li>User should be informed moon was not added to planetarium</li>
            </ol>
        </td>
        <td>Moon not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>26</td>
        <td>Given a non-unique moon name, invalid planet id, and no image a user should not be able to add the moon to planetarium</td>
        <td>N/A</td>
        <td>non-unique moon name, invalid planet id, no image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide non-unique moon name</li>
                <li>Provide invalid planet id</li>
                <li>Provide no image</li>
                <li>User should be informed moon was not added to planetarium</li>
            </ol>
        </td>
        <td>Moon not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>27</td>
        <td>Given a non-unique moon name, invalid planet id, and valid image a user should not be able to add the moon to planetarium</td>
        <td>N/A</td>
        <td>non-unique moon name, invalid planet id, valid image</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide non-unique moon name</li>
                <li>Provide invalid planet id</li>
                <li>Provide valid image</li>
                <li>User should be informed moon was not added to planetarium</li>
            </ol>
        </td>
        <td>Moon not added to planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>28</td>
        <td>Given a existing planet name a user should be able to remove the planet from the planetarium</td>
        <td>Planet with name "Furina" in planetarium</td>
        <td>existing planet name</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide existing planet name</li>
                <li>User should be informed planet was removed from planetarium</li>
            </ol>
        </td>
        <td>Planet removed from planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>29</td>
        <td>Given a non-existing planet name a user should not be able to remove the planet from the planetarium</td>
        <td>No planet with name "Beidou" in planetarium</td>
        <td>non-existing planet name</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide non-existing planet name</li>
                <li>User should be informed planet was not removed from planetarium</li>
            </ol>
        </td>
        <td>Planet not removed from planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>30</td>
        <td>Given a existing moon name a user should be able to remove the moon from the planetarium</td>
        <td>Moon with name "Fischl" in planetarium</td>
        <td>existing moon name</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide existing moon name</li>
                <li>User should be informed moon was removed from planetarium</li>
            </ol>
        </td>
        <td>Moon removed from planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
    <tr>
        <td>31</td>
        <td>Given a non-existing moon name a user should not be able to remove the moon from the planetarium</td>
        <td>No moon with name "Layla" in planetarium</td>
        <td>non-existing moon name</td>
        <td>
            <ol>
                <li>Successfully login</li>
                <li>Provide non-existing moon name</li>
                <li>User should be informed moon was not removed from planetarium</li>
            </ol>
        </td>
        <td>Moon not removed from planetarium</td>
        <td>TBD</td><td>Kevin</td><td>In Progress</td>
    </tr>
</table>
