# skill_navigator
# Problem Statement

1. The technology industry is evolving rapidly, creating a persistent gap between the skills of graduating students and the competencies demanded by employers.  
2. Traditional career counseling and skill assessment methods are manual, time-consuming, and fail to provide personalized, actionable guidance at scale.  
3. Students often graduate underprepared for their target job roles, while employers struggle to find candidates with both technical and soft skills aligned to industry needs.  
4. Learners lack motivation and accountability due to the absence of structured, interactive, and personalized learning pathways.  
5. There is a pressing need for an **AI-powered solution** that can:  
   - Analyze student skill profiles.  
   - Identify technical and soft skill gaps.  
   - Generate personalized learning roadmaps.  
   - Recommend free, accessible learning resources.  
   - Provide interactive dashboards, scheduled calendars, and real-time progress tracking to keep learners motivated and accountable.
  
   
# Novelty of the work
1. **Integrated Dual-Domain Assessment**  
   - Unlike existing tools that focus only on technical or soft skills, this platform uniquely integrates both domains.  
   - Students receive a complete picture of job readiness, covering technical competencies and behavioral soft skills.  

2. **Generative AI-Driven Personalization**  
   - Uses the Google Gemini Generative AI API to dynamically generate customized learning roadmaps.  
   - Recommendations are contextualized based on the student’s existing skills, target job role, and identified gaps.  
   - Provides highly personalized guidance beyond static, rule-based systems.  

3. **Scenario-Based Soft Skills Quantification**  
   - Employs interactive, scenario-based quizzes instead of simple self-ratings.  
   - Produces a nuanced and reliable assessment of soft skills like communication, teamwork, and leadership.  
   - Generates targeted development recommendations for specific lagging skills.  

4. **Leisure-Time-Aware Learning Scheduler**  
   - Introduces a novel scheduling paradigm that adapts to the student’s declared leisure time.  
   - Respects academic and personal commitments, making adherence more feasible.  

5. **Zero-Cost Resource Commitment**  
   - All recommended learning resources (books, YouTube channels, courses, communities) are entirely free.  
   - Ensures equitable access for students from diverse socioeconomic backgrounds.  

6. **Real-Time Dynamic Analysis**  
   - Any modification to the skill list (addition/removal) instantly triggers re-analysis.  
   - Updates Skill Score, missing skills list, and roadmap in real time without page reload.  
   - Creates an interactive, exploratory experience that motivates students to experiment and learn.  
##  Requirement Specification

###  Functional Requirements

**FR-01: Skill Input & Validation**  
- Accept one or more current skills as interactive tag inputs.  
- Minimum of one skill required; inline error if none entered.  
- Adding/removing a skill triggers immediate real-time re-analysis.  

**FR-02: Job Goal Selection**  
- Provide a searchable dropdown of target job roles (e.g., Data Scientist, Frontend Developer).  
- Changing job goal automatically refreshes Skill Score and results.  

**FR-03: Skill Score & Gap Analysis**  
- Compute and display job-readiness Skill Score as an animated percentage gauge.  
- Color coding: Red (0–40%), Amber (41–70%), Green (71–100%).  
- List missing skills as categorized cards with importance levels (High/Medium/Low).  

**FR-04: Technical Learning Roadmap**  
- Generate structured roadmap (Beginner → Intermediate → Advanced) for each missing skill.  
- Each step includes estimated completion time and free learning resource links.  
- Roadmap cards are expandable/collapsible with progress indicators.  

**FR-05: Soft Skills Assessment Quiz**  
- Present scenario-based quiz assessing soft skills relevant to job role.  
- Questions appear one at a time with progress bar and smooth transitions.  
- Supported formats: Multiple Choice, Likert Scale (Strongly Agree → Strongly Disagree).  

**FR-06: Soft Skills Results & Roadmap**  
- Display proficiency scores for each assessed soft skill.  
- Generate personalized roadmap with free resources (books, YouTube, communities, courses).  

**FR-07: Learning Dashboard & Scheduler**  
- Accept user’s leisure time slots to generate weekly/monthly learning calendar.  
- Sessions color-coded by category (technical vs. soft skills).  

**FR-08: Deadline Alerts & Timers**  
- Allow users to set deadlines for courses/tasks.  
- Countdown timers show time remaining.  
- Alerts notify when deadlines are 3 days away or missed.  
- Deadlines can be edited or reset anytime.  

**FR-09: Free Learning Platform Suggestions**  
- Display curated list of free learning platforms.  
- Each entry includes: name, logo/icon, description, skill types, direct link.  
- All platforms must be completely free (no mandatory payment/subscription).  

**FR-10: Closing / Farewell Screen**  
- Show encouraging farewell message after roadmap/dashboard setup.  
- Include CTA to return to dashboard or restart analysis.  

### Non-Functional Requirements

**NFR-01: Performance**  
- Skill Score and gap analysis must update within 3 seconds of any skill modification.  

**NFR-02: Reliability**  
- Application must handle all interactions (skill add/remove, quiz navigation) without errors.  

**NFR-03: Usability**  
- UI must be intuitive, visually engaging, and easy to navigate.  

##  Methodology

### **Phase 1: Requirements Analysis**
- Conducted stakeholder interviews and surveys with students and faculty to identify career preparation pain points.  
- Analyzed existing tools (LinkedIn Learning, Coursera Career Academy, SkillRoads) to identify feature gaps.  
- Documented functional and non-functional requirements in a structured Software Requirements Specification (SRS).  
- Researched and identified free learning platforms for both technical and soft skills.  

### **Phase 2: System Design**
- Designed a three-tier architecture:  
  - **Presentation Layer**: HTML/CSS/JavaScript  
  - **Application Layer**: Flask  
  - **AI Integration Layer**: Gemini API  
- Created detailed wireframes and UI mockups using Figma.  
- Designed database schema for user sessions, skills, quiz responses, and calendar data.  
- Defined Gemini API prompt engineering strategy for skill gap analysis and roadmap generation.  

### **Phase 3: Implementation**
- Developed Flask backend with RESTful API endpoints for skill analysis, quiz evaluation, and calendar generation.  
- Integrated Gemini API with structured JSON parsing and error handling.  
- Built interactive frontend with:  
  - Dynamic skill tag inputs  
  - Animated Skill Score gauge  
  - Real-time update listeners  
  - Quiz flow engine  
- Developed Learning Dashboard with JavaScript-based calendar renderer and countdown timer engine.  
- Implemented alert notification system for deadlines and overdue tasks.  

### **Phase 4: Integration & Testing**
- Performed unit testing on API endpoints and frontend components.  
- Conducted integration testing to ensure seamless communication between backend, frontend, and Gemini API.  
- Validated real-time updates and error-free user interactions.  

### **Phase 5: Deployment**
- Deployed the application on a cloud-based environment for accessibility.  
- Configured continuous monitoring and logging for performance and reliability.  
- Ensured scalability and availability for multiple concurrent users.  

##  System Design

### System Architecture (Three-Tier MVC)
1. **Presentation Layer (View)**  
   - Technology: HTML5, CSS3, JavaScript (ES6+)  
   - Components: Dynamic skill tag input, animated SVG Skill Score gauge, interactive quiz flow, calendar renderer, countdown timers  
   - Communication: Asynchronous Fetch API calls (JSON over HTTP)  

2. **Application Layer (Controller)**  
   - Technology: Python 3.10+, Flask 3.x  
   - Responsibilities: Route handling, request validation, Gemini API prompt construction, response parsing, scheduling algorithm  
   - Endpoints: `/analyze`, `/quiz-evaluate`, `/generate-roadmap`, `/schedule-calendar`  

3. **AI Integration Layer (Model)**  
   - Technology: Google Gemini API (gemini-1.5-flash)  
   - Responsibilities: Semantic skill gap analysis, roadmap generation, soft skill evaluation, free resource suggestions  
   - Response Format: Structured JSON validated by Flask backend before frontend rendering  

 # Page Architecture
- **Landing Page** → Animated hero section, feature highlights, CTA to analysis  
- **Skill Gap Analysis (/analyze)** → Skill tag input, job goal selector, Skill Score gauge, missing skills list  
- **Technical Roadmap (/analyze#roadmap)** → Roadmap cards per skill, free resource links, progress indicators  
- **Soft Skills Assessment (/soft-skills)** → Scenario-based quiz, progress bar, smooth navigation  
- **Soft Skills Results (/soft-skills#results)** → Proficiency breakdown, lagging skills, personalized roadmap  
- **Learning Dashboard (/dashboard)** → Leisure time input, weekly/monthly calendar, deadline timers, alerts  
- **Platform Directory (/dashboard#platforms)** → Curated free platform cards (name, description, category, link)  
- **Farewell Screen (/farewell)** → Motivational closing message, restart/dashboard CTA  

### ** Data Flow (Textual Representation)**
1. User inputs skills and selects job goal.  
2. Frontend sends POST request to `/analyze`.  
3. Flask backend constructs structured prompt with skills + job role.  
4. Gemini API returns JSON (Skill Score, missing skills, roadmaps).  
5. Backend validates and parses JSON → sends to frontend.  
6. Frontend renders Skill Score gauge, missing skills, roadmap.  
7. User takes Soft Skills Quiz → responses sent to `/quiz-evaluate`.  
8. Gemini returns proficiency scores for soft skills.  
9. User inputs leisure time → `/schedule-calendar` generates calendar.  
10. Frontend renders calendar + countdown timers.  


### ** Key Design Decisions**
- **Gemini API for AI analysis** → Provides advanced semantic skill matching with structured JSON output.  
- **Flask Backend** → Lightweight, Python-native, supports rapid RESTful API development.  
- **Client-Side Real-Time Updates** → Eliminates page reloads, ensures fluid and responsive UX.  
- **Free-Only Resource Policy** → Guarantees equitable access, aligns with social impact mission.  
- **Scenario-Based Quiz Design** → More reliable than self-rating, reduces bias, produces actionable data.  
- **Leisure-Time-Driven Scheduling** → Fits learning into student routines, increases adherence.

##  Conclusion

1. **Advancement in Career Readiness Tools**  
   - The GenAI-Assisted Skill Gap Analyzer represents a meaningful step forward in AI-powered career preparation for students.  
   - Combines semantic intelligence of Google Gemini Generative AI API with a user-friendly design.  

2. **Holistic Dual-Domain Approach**  
   - Integrates both technical competencies and corporate soft skills in one platform.  
   - Provides comprehensive guidance aligned with employer expectations.  

3. **Active Learning Companion**  
   - Leisure-time-aware scheduler, deadline countdown timers, and in-app alerts transform the tool from passive assessment into an active learning companion.  

4. **Equitable Access Philosophy**  
   - Commitment to recommending only free, open-access resources.  
   - Removes financial barriers, democratizing career preparation for all students.  

5. **Generative AI Impact**  
   - Demonstrates that Generative AI can deliver personalized, contextually relevant, and actionable career guidance.  
   - Provides services previously accessible only through costly career coaching or enterprise HR platforms.  

6. **Future Enhancements**  
   - Resume gap analysis.  
   - Mock interview simulations.  
   - Peer learning communities.  
   - Integration with job portal APIs for real-time job market insights.  

7. **Foundation for Career Ecosystem**  
   - Establishes a scalable, end-to-end career readiness ecosystem.  
   - Designed to serve students at scale with personalized, actionable learning journeys.  

