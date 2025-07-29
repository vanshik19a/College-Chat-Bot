College Chat Bot
An AI-powered system designed to assist consumers by analyzing product warranties, detecting unfair clauses, retrieving relevant consumer protection laws, and generating formal complaint letters. This application bridges the gap between legal knowledge and accessibility by utilizing advanced AI and NLP technologies.

Abstract
This project aims to simplify and automate the process of understanding product warranties and consumer rights using Artificial Intelligence. Many consumers face challenges in interpreting complex warranty documents or identifying misleading or unfair terms. To address this, the system performs optical character recognition (OCR) on scanned contracts, analyzes clauses for legal fairness using AI models, retrieves applicable laws, and generates formal complaint letters based on identified violations. The tool integrates modern AI frameworks like LangChain and Gemini, legal knowledge bases, and database systems to deliver a seamless consumer support experience.

Key Features
Document Processing (OCR):
Extracts text from scanned or image-based contracts using Tesseract OCR, enabling support for physical document uploads.

Clause Analysis (NLP & AI):
Uses LangChain and Google's Gemini AI to analyze contracts and identify potentially unfair or deceptive terms based on predefined legal parameters.

Legal Knowledge Retrieval:
Matches flagged content with relevant consumer protection laws to justify legal validity, referencing applicable statutes.

Automated Complaint Generation:
Automatically formulates formal complaint letters based on identified unfair terms, suitable for submission to companies or legal authorities.

Voice-Based Complaint Input (Upcoming):
Plans for future integration of voice-to-text input for complaint logging and submission, increasing accessibility.

System Requirements
Hardware Requirements
Operating System: Windows 10/11 or Linux/Mac

RAM: 4 GB or higher

Processor: Dual Core or above

Storage: 1 GB minimum available space

Software Requirements
Node.js and npm

Python 3.8+

Supabase account

Google Gemini API key

Tesseract OCR

React, Express, Tailwind CSS, LangChain, PostgreSQL

Project Architecture
The system is designed using the Model-View-Controller (MVC) pattern for scalability and maintainability. It includes a React frontend, an Express backend, Python modules for AI, and Supabase as the cloud database.

User Interface (React)
     ↓
API Server (Node.js + Express)
     ↓
AI/NLP Processing (Python with Gemini + LangChain)
     ↓
Supabase DB (PostgreSQL)


Directory Structure
/client         → React + TailwindCSS frontend
/server         → Express.js backend API
/shared         → Common type definitions and validators
/migrations     → SQL scripts for Supabase DB setup

Setup Instructions
Step 1: Clone the Repository
git clone <repository-url>
cd consumer-protection-assistant

Step 2: Configure Environment
cp .env.example .env

Edit .env with your API keys:
GEMINI_API_KEY=your_gemini_api_key
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_KEY=your_supabase_anon_key
PORT=3000
NODE_ENV=development

Step 3: Set up Supabase Database
Log into your Supabase project and run the following SQL in the SQL editor:
-- Create documents table
create table documents (
  id serial primary key,
  file_name text not null,
  content text not null,
  status text not null default 'pending',
  analysis jsonb,
  uploaded_at timestamp default now()
);

-- Create complaints table
create table complaints (
  id serial primary key,
  document_id integer references documents(id),
  content text not null,
  is_voice_input boolean default false,
  created_at timestamp default now()
);

Step 4: Install Dependencies
npm install
pip install -r requirements.txt

Step 5: Run Setup Script
chmod +x setup.sh
./setup.sh

Step 6: Start Development Server
npm run dev

Visit the application at http://localhost:3000

Modules Overview
1. OCR Module
Technology: Python, Tesseract OCR

Function: Converts images to plain text for further processing

2. Clause Detection Module
Technology: LangChain + Gemini AI

Function: Detects legally unfair or ambiguous clauses from input text

3. Law Matching Engine
Technology: LangChain retriever module

Function: Maps clauses to relevant consumer protection laws

4. Complaint Generator
Technology: NLG + Template-based generation

Output: Custom legal complaint letter including document references and legal justifications

5. Database Handler
Technology: Supabase/PostgreSQL

Stores: Uploaded documents, analysis results, complaint history

Planned Future Enhancements
Integration with Indian Consumer Complaint Portal for direct submission

Voice-to-text input using Whisper or Gemini Multimodal API

Support for multiple languages (Hindi, Tamil, etc.)

User login and case tracking dashboard

