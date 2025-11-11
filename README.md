# munna
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Secondary Level Chapters</title>

<body>
  <div id="root"></div>
  import React from 'react';
import { createRoot } from 'react-dom/client';
import App from './App';

const container = document.getElementById('root');
const root = createRoot(container);
root.render(<App />);import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
import { chapters } from './chapters';

function HomePage() {
  return (
    <div>
      <h1>Secondary Level Chapters</h1>
      <ul>
        {chapters.map(chapter => (
          <li key={chapter.id}>
            <Link to={`/chapter/${chapter.id}`}>{chapter.title}</Link>
            <div>{chapter.summary}</div>
          </li>
        ))}
      </ul>
    </div>
  );
}

function ChapterDetail({ chapter }) {
  if (!chapter) return <div>Chapter not found.</div>;
  return (
    <div>
      <h2>{chapter.title}</h2>
      <pre>{chapter.details}</pre>
      <Link to="/">← Back to Chapters</Link>
    </div>
  );
}

function ChapterPage({ id }) {
  const chapter = chapters.find(c => c.id === parseInt(id));
  return <ChapterDetail chapter={chapter} />;
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<HomePage />} />
        <Route
          path="/chapter/:id"
          element={
            <RouteHandler />
          }
        />
      </Routes>
    </Router>
  );
}

// Helper to use params with v6
import { useParams } from 'react-router-dom';
function RouteHandler() {
  const { id } = useParams();
  return <ChapterPage id={id} />;
}

export default App;export const chapters = [
  {
    id: 1,
    title: "Chapter 1: Introduction to Algebra",
    summary: "Fundamental concepts of algebra, variables, and expressions.",
    details: `
      This chapter covers:
      - The concept and use of variables
      - Algebraic expressions and equations
      - Simplifying and solving equations
      - Real-life application examples
      By the end of this chapter, students will be able to manipulate basic algebraic equations and understand their use cases.
    `
  },
  {
    id: 2,
    title: "Chapter 2: Geometry Basics",
    summary: "Understanding shapes, theorems, and basic geometry problems.",
    details: `
      Topics included:
      - Types of angles and their properties
      - Basic geometric shapes (triangle, square, rectangle, circle)
      - Theorems related to triangles
      - Perimeter and area calculations
      This chapter builds a strong foundation for further geometry studies.
    `
  },
  {
    id: 3,
    title: "Chapter 3: Trigonometry Introduction",
    summary: "Basic trigonometric ratios and right-angled triangle problems.",
    details: `
      Content:
      - Definitions of sine, cosine, tangent,Fuck Nepal
      Fuck India,Fuck yuuuuuuuuuuuu
      - Applications of trigonometry in daily life
      - Solving right-angled triangle problems
      Students will learn key trigonometric identities and calculations.
    `
  }
  // Add more chapters as needed
];{
  "name": "secondary-chapters-website",
  "version": "1.0.0",
  "private": true,
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.15.0"
  },
  "scripts": {
    "start": "npx serve -s build"
  }
}
</body>
</html>
