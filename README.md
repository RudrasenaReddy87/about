<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mail & Profile</title>
  <link rel="stylesheet" href="mail.css">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">

  <style>

body {
  font-family: 'Inter', sans-serif;
  background-color: #f8fafc;
  margin: 0;
  padding: 2rem;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Container Styles */
.coding-profiles-container {
  max-width: 1200px;
  width: 100%;
  padding: 2rem;
  background-color: white;
  border-radius: 16px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
  perspective: 1000px; /* For 3D effects */
}

.section-title {
  text-align: center;
  color: #1e293b;
  margin-bottom: 3rem;
  font-size: 2.25rem;
  font-weight: 600;
  position: relative;
  padding-bottom: 1rem;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 4px;
  background: linear-gradient(90deg, #6366f1, #8b5cf6);
  border-radius: 2px;
}

/* Profile Grid Layout */
.profiles-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

/* Profile Card - Base Styles */
.profile-card {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 2rem;
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  overflow: hidden;
  text-decoration: none;
  color: #1e293b;
  z-index: 1;
  height: 140px;
  border: 1px solid #e2e8f0;
  transform-style: preserve-3d;
  animation: float 6s ease-in-out infinite;
}

/* Floating Animation */
@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

/* Text Styles */
.profile-name {
  font-weight: 600;
  font-size: 1.25rem;
  transition: all 0.3s ease;
  margin-bottom: 0.5rem;
  position: relative;
  display: inline-block;
}

.profile-name::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: currentColor;
  transition: width 0.3s ease 0.1s;
}

.profile-link {
  font-size: 0.9rem;
  color: #64748b;
  transition: all 0.3s ease;
  line-height: 1.4;
}

/* Hover Effect - Gradient Slide */
.hover-effect {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -2;
  transform: translateY(101%);
  transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  opacity: 0.95;
  background-size: 200% 200%;
}

/* Gradient Pulse Animation */
@keyframes gradientPulse {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

/* Border Light Effect */
.profile-card::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: linear-gradient(
    to bottom right,
    transparent 45%,
    rgba(255,255,255,0.5) 50%,
    transparent 55%
  );
  transform: rotate(45deg);
  transition: all 0.6s ease;
  opacity: 0;
  z-index: -1;
}

@keyframes borderLight {
  0% { transform: rotate(45deg) translate(-30%, -30%); }
  100% { transform: rotate(45deg) translate(30%, 30%); }
}

/* Text Wave Animation */
@keyframes waveText {
  0%, 100% { transform: translateY(0); }
  25% { transform: translateY(-5px); }
  50% { transform: translateY(3px); }
  75% { transform: translateY(-2px); }
}

/* Hover States */
.profile-card:hover {
  transform: translateY(-8px) rotateX(5deg) rotateY(5deg);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
  animation: none;
}

.profile-card:hover .hover-effect {
  transform: translateY(0);
  animation: gradientPulse 4s ease infinite;
}

.profile-card:hover .profile-name::after {
  width: 100%;
}

.profile-card:hover .profile-name {
  animation: waveText 0.8s ease;
}

.profile-card:hover .profile-link {
  color: rgba(255, 255, 255, 0.9);
}

.profile-card:hover::before {
  animation: borderLight 1.2s ease;
  opacity: 1;
}

/* Platform-Specific Colors */
.email .hover-effect { 
  background: linear-gradient(135deg, #d44638 0%, #e74c3c 100%); 
}
.leetcode .hover-effect { 
  background: linear-gradient(135deg, #ffa116 0%, #f39c12 100%); 
}
.geeksforgeeks .hover-effect { 
  background: linear-gradient(135deg, #2F8D46 0%, #27ae60 100%); 
}
.codechef .hover-effect { 
  background: linear-gradient(135deg, #7A5C58 0%, #6c5c7b 100%); 
}
.hackerrank .hover-effect { 
  background: linear-gradient(135deg, #00EA64 0%, #2ecc71 100%); 
}
.hackerearth .hover-effect { 
  background: linear-gradient(135deg, #2C3454 0%, #34495e 100%); 
}

/* Text Color on Hover */
.email:hover { color: white; }
.leetcode:hover { color: white; }
.geeksforgeeks:hover { color: white; }
.codechef:hover { color: white; }
.hackerrank:hover { color: white; }
.hackerearth:hover { color: white; }

/* Responsive Design */
@media (max-width: 768px) {
  .profiles-grid {
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  }
  
  .profile-card {
    height: 120px;
    padding: 1.5rem;
  }
}

@media (max-width: 480px) {
  body {
    padding: 1rem;
  }
  
  .coding-profiles-container {
    padding: 1.5rem;
  }
  
  .section-title {
    font-size: 1.75rem;
    margin-bottom: 2rem;
  }
  
  .profiles-grid {
    grid-template-columns: 1fr;
  }
  
  .profile-card {
    height: 110px;
    padding: 1.25rem;
  }
  
  .profile-name {
    font-size: 1.1rem;
  }
  
  .profile-link {
    font-size: 0.8rem;
  }
}
  </style>
</head>
<body>
  <div class="coding-profiles-container">
    <h2 class="section-title">My Coding Profiles</h2>
    <div class="profiles-grid">
      <!-- Gmail (opens in same tab) -->
      <a href="b.rudrasenareddy@gmail.com" class="profile-card email">
        <span class="profile-name">Here My Mail</span>
        
        <span class="profile-link">b.rudrasenareddy@gmail.com</span>
        <div class="hover-effect"></div>
      </a>

      <!-- LeetCode -->
      <a href="https://leetcode.com/u/rudrasenareddy/" 
         class="profile-card leetcode"
         target="_blank" 
         rel="noopener noreferrer">
        <span class="profile-name">LeetCode</span>
        <span class="profile-link">leetcode.com/u/rudrasenareddy</span>
        <div class="hover-effect"></div>
      </a>

      <!-- GeeksforGeeks -->
      <a href="https://www.geeksforgeeks.org/user/brudrasenareddy/" 
         class="profile-card geeksforgeeks"
         target="_blank" 
         rel="noopener noreferrer">
        <span class="profile-name">GeeksforGeeks</span>
        <span class="profile-link">geeksforgeeks.org/user/brudrasenareddy</span>
        <div class="hover-effect"></div>
      </a>

      <!-- CodeChef -->
      <a href="https://www.codechef.com/users/rudrasenareddy" 
         class="profile-card codechef"
         target="_blank" 
         rel="noopener noreferrer">
        <span class="profile-name">CodeChef</span>
        <span class="profile-link">codechef.com/users/rudrasenareddy</span>
        <div class="hover-effect"></div>
      </a>

      <!-- HackerRank -->
      <a href="https://www.hackerrank.com/profile/RudraSenaReddy" 
         class="profile-card hackerrank"
         target="_blank" 
         rel="noopener noreferrer">
        <span class="profile-name">HackerRank</span>
        <span class="profile-link">hackerrank.com/profile/RudraSenaReddy</span>
        <div class="hover-effect"></div>
      </a>

      <!-- HackerEarth -->
      <a href="https://www.hackerearth.com/@Rudrasenareddy" 
         class="profile-card hackerearth"
         target="_blank" 
         rel="noopener noreferrer">
        <span class="profile-name">HackerEarth</span>
        <span class="profile-link">hackerearth.com/@Rudrasenareddy</span>
        <div class="hover-effect"></div>
      </a>
    </div>
  </div>
</body>
</html>
