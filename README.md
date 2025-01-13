<h1 align="center"><strong>Youtube Chronicle</strong><br>YouTube Summary Workflow using n8n</h1>

<!-- <p align="center">
  <img src="screenshot.jpg" alt="Screenshot">
</p> -->

<p align="center">
  <a href="https://youtu.be/MXI7vt8lXD4">
    <img src="https://img.youtube.com/vi/MXI7vt8lXD4/0.jpg" alt="Youtube Video">
  </a>
</p>

<p align="center">
  <a href="https://youtu.be/MXI7vt8lXD4">Youtube Chronicle</a>
</p>
This n8n workflow authenticates users, retrieves data from YouTube channels, and generates a dynamic webpage summarizing the latest YouTube videos from the user's favorite channels. The workflow is designed for efficient automation with error handling and session management.

## Features  

### 1. **User Authentication**  
- Supports user login via **Google Sheets**, **Firestore**, or **Supabase** databases.  
- Credentials (username and password) must be pre-created in the database.  
- If login fails, the user is notified and redirected to the login page with the option to retry.  

### 2. **Main Page Functionality**  
- After successful login, the user is presented with a **main page** containing an accordion menu with 5 input fields for YouTube channel handles.  
- The user specifies their favorite YouTubers by providing channel handles in these fields.  
- Upon submission, the data is stored in the database for future sessions.  

### 3. **Data Collection and Processing**  
- On subsequent logins, the workflow retrieves:  
  - The two latest videos for each YouTube channel specified.  
  - Transcripts of the videos using the **YouTube Transcript community node**.  
- Summaries of the video transcripts are generated and presented on the webpage, organized by YouTuber.  
- Links to the original videos and channels are provided for easy access.  

### 4. **Dynamic and Configurable**  
- The number of videos retrieved can be adjusted by changing the `maxResults` parameter in the workflow.  
- The workflow is fully dynamic, allowing additional favorite channels to be configured.  

### 5. **Session Management**  
- **Logout:** Users can log out using the logout button, returning to the login page, and terminating the workflow.  
- **Inactivity:** If the user spends more than 5 minutes on the page, the submit button becomes disabled, and the workflow automatically terminates.  
- **Window Closure:** If the browser window is closed or left open for too long, the same behavior as inactivity occurs.  

### 6. **Error Handling**  
- Basic error handling is implemented to manage invalid YouTube channel handles or API errors.  

## Prerequisites  
To set up and run this workflow, you will need:  

1. **Google OAuth** for YouTube API.  
2. **Google Sheets** or **Firestore** (optional if using Supabase for user data).  
3. **Supabase API Key** (if using Supabase for database management).  
4. **LLM API Key** (e.g., **Groq**, though this can be replaced with another provider).  

## Data Storage  
The workflow utilizes two database tables:  
1. **User Credentials Table:** Stores usernames and passwords for authentication.  
2. **User Preferences Table:** Stores the user's favorite YouTube channel handles.  

## Workflow Steps  

1. **Start the Workflow:**  
   - Display a login page where users enter their credentials.  
   - Authenticate credentials against the chosen database (Google Sheets, Firestore, or Supabase).  
   - Redirect users to the main page upon successful login or notify them of failure.  

2. **Main Page Interaction:**  
   - Present an accordion menu for entering up to 5 favorite YouTube channels.  
   - Save the entered channel handles to the database upon submission.  

3. **Retrieve and Summarize Data:**  
   - Fetch the latest two videos for each channel.  
   - Retrieve video transcripts using the **YouTube Transcript community node**.  
   - Generate summaries and organize them by YouTuber on the webpage.  
   - Provide clickable links to the original videos and channels.  

4. **Session and Error Management:**  
   - Terminate the session after 5 minutes of inactivity or upon window closure.  
   - Handle invalid input gracefully and notify users of errors.  

5. **Logout:**  
   - Allow users to log out, clearing session data and returning to the login page.  

## Customization  

To customize the workflow:  
- Modify the `maxResults` parameter in the "Get data of the latest videos" node to adjust the number of videos retrieved.  
- Change the LLM API provider if needed by updating the API key and relevant configurations.  
- Expand error handling or styling options as required.  

## Technology Stack  

This workflow integrates the following tools and APIs:  
- **n8n** for workflow automation.  
- **Google Sheets / Firestore / Supabase** for database management.  
- **YouTube API** for video and transcript retrieval.  
- **Groq (or other LLM API)** for transcript summarization.

## More automation and n8n
[Complete Gouid How to Create an AI Generated News Website](https://www.youtube.com/playlist?list=PL0dJpoLxZYoFGMFqQVCsgiCVujoNh1VxP)
