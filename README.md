# AI Code Review Assistant

Internship-level full-stack project for reviewing pasted source code and uploaded source files with authentication, static analysis, AI review suggestions, complexity metrics, and a searchable review dashboard.

## Implemented Features

- User authentication: sign up, login, logout, forgot-password demo flow, and profile management.
- Code submission: paste source code and upload source code files.
- GitHub repository URL: intentionally disabled because this version is not working on GitHub integration.
- Static code analysis: syntax-risk checks, unused variables/imports, missing error handling, duplicate blocks, formatting/style warnings, debug statements, and basic security warnings.
- AI code review: uses OpenAI when `OPENAI_API_KEY` is configured, otherwise falls back to local heuristic recommendations.
- Complexity analysis: cyclomatic complexity, function complexity, file complexity, number of functions, number of classes, and lines of code.
- Review dashboard: previous reviews, search, severity filter, delete, and detailed reports.

## Learning Outcomes

By completing this project, students gain practical experience in:

- Full-stack application development
- Authentication and authorization
- Database design
- REST API development
- GitHub API integration awareness, though GitHub review is not implemented in this version
- AI API integration
- Static code analysis
- File uploads
- Error handling
- Clean architecture
- Asynchronous programming
- Responsive UI design
- Deployment to cloud platforms
- Professional documentation

## Bonus Features

Advanced students can extend the core project with:

- Multi-language support for JavaScript, Python, Java, C++, and more
- GitHub OAuth login
- Pull request review integration
- Team workspaces
- Real-time collaboration
- AI-powered refactoring suggestions
- Code quality scoring from 0 to 100
- Interactive charts and analytics
- Dark and light themes
- Email notifications after review completion
- CI/CD integration with GitHub Actions
- Docker support
- Admin dashboard
- Leaderboard for code quality improvement

## Expected Deliverables

Each student should submit:

- Source code for frontend and backend
- GitHub repository
- Database schema
- API documentation
- README file
- Deployment link
- Demo video of 3 to 5 minutes
- Sample test cases

## Tech Stack

- Frontend: React + Vite
- Styling: custom responsive CSS
- Backend: Node.js + Express.js
- Storage: local JSON files for a lightweight internship demo
- Authentication: JWT + bcrypt password hashing
- AI integration: OpenAI Chat Completions API via `fetch`
- File upload: Multer

## Project Structure

```text
server/
  index.js                 API routes and auth middleware
  services/
    aiReview.js            OpenAI integration and fallback AI-style review
    staticAnalyzer.js      Static analysis and complexity metrics
    storage.js             Local JSON persistence
src/
  main.jsx                 React application
  styles.css               App styling
```

## Setup

```bash
npm install
copy .env.example .env
npm run dev
```

The frontend runs at `http://localhost:5173` and proxies API calls to `http://localhost:5000`.

For AI-powered reviews, add an OpenAI key to `.env`:

```text
OPENAI_API_KEY=your_api_key_here
OPENAI_MODEL=gpt-4o-mini
```

Without an API key, reviews still work using the local fallback reviewer.

## Database Design Mapping

The demo uses JSON files with the same shape as the proposed database tables:

- `users`: `id`, `name`, `email`, `passwordHash`, `created_at`
- `projects`: `id`, `user_id`, `project_name`, `github_url`, `created_at`
- `reviews`: `id`, `project_id`, `review_type`, `overall_score`, `summary`, `metrics`, `recommendations`, `created_at`
- `findings`: `id`, `review_id`, `severity`, `issue`, `explanation`, `suggested_fix`, `file_name`, `line_number`

For production, replace `server/services/storage.js` with PostgreSQL or Supabase queries while keeping the API contract mostly unchanged.

## Conclusion

The AI Code Review Assistant is a practical, industry-relevant project that mirrors tools used in professional software development environments. It combines modern web technologies with artificial intelligence to automate code reviews, helping developers write cleaner, more efficient, and better-documented code.

Unlike a basic CRUD application, this project challenges students to work with API integration, AI services, static analysis, authentication, and scalable application architecture. It encourages problem-solving, software engineering best practices, and clean coding principles.

By the end of the project, students will have built a portfolio-worthy application that demonstrates their ability to design, develop, and deploy a modern AI-powered web application, making it useful as an internship assessment and as a resume project.
