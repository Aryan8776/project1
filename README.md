Child Health Portal

A modern and secure child health management system built with HTML, CSS, JavaScript, and Supabase.
It includes user authentication, vaccination tracking, appointment management, and a personal health dashboard.

🚀 Live Features
1. Authentication System

(From index.html 

index

)

Login and Sign-up tabs

Supabase email/password authentication

Password confirmation validation

User metadata saved (name, email, password)

Auto-redirect if already logged-in

Smooth UI with dark modern theme

2. Child Health Dashboard

(From dashboard.html 

dashboard

)

Virtual ID card with name + parent email

Vaccination Records

Add vaccine name, scheduled date, given date, status

Auto-load vaccination table

RLS-secured database records

Appointments Module

Add appointment date, purpose, doctor, status

Auto-load appointment records

User Profile Icon (initial from email)

Logout button

Mobile-responsive UI and animated background

📁 Project Structure
child-health-portal/
│
├── public/
│   ├── index.html          # Login & Signup page (Supabase Auth)
│   ├── dashboard.html      # Main health dashboard
├── README.md               # Repository documentation


🗄️ Supabase Setup
Tables Required
users table
id uuid primary key
name text
email text
password text
inserted_at timestamp default now()

vaccinations table
id uuid default uuid_generate_v4()
user_id uuid default auth.uid()
vaccine text
scheduled_date date
given_date date
status text
inserted_at timestamp default now()

appointments table
id uuid default uuid_generate_v4()
user_id uuid default auth.uid()
date date
purpose text
doctor text
status text
inserted_at timestamp default now()

🔒 Row-Level Security (RLS)
Enable RLS on:

users

vaccinations

appointments

Select Policy
create policy "Allow users to read their data"
on vaccinations for select
using ( auth.uid() = user_id );

Insert Policy
create policy "Allow users to insert their data"
on vaccinations for insert
with check ( auth.uid() = user_id );


Repeat the same for appointments.

⚙️ Environment Variables (If Deploying on Vercel)

Add:

SUPABASE_URL=(https://hfytpmyqvdzdehembdpr.supabase.co)
SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImhmeXRwbXlxdmR6ZGVoZW1iZHByIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjIzNTg3NzIsImV4cCI6MjA3NzkzNDc3Mn0.IBvAlibQX4ZpQeC1FMTPgPaD-2odx42Ec0CkilSGA4Y

▶️ How to Run Locally

Download/clone the repository

Open the folder in VS Code

Start with Live Server or double-click:

public/index.html


Login or create an account

You will be redirected to:

public/dashboard.html

🌟 Future Enhancements

Child photo upload

Medical history module

Diet & nutrition tracking

PDF export of health records

Reminder notifications

🙌 Author

Built using Supabase + HTML/CSS/JS
