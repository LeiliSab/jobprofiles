<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Alumni Profiles and Skill Development</title>
    <style>
    /* Inline CSS */

    body {
        font-family: Arial, sans-serif;
        margin: 20px;
    }

    h1 {
        text-align: center;
    }

    .profile {
        border: 1px solid #ccc;
        padding: 15px;
        margin-bottom: 15px;
    }

    .profile h2 {
        margin-top: 0;
    }

    .skills, .courses {
        list-style-type: none;
        padding: 0;
    }

    .skills li, .courses li {
        background-color: #f9f9f9;
        margin: 5px 0;
        padding: 5px;
    }

    .courses li a {
        text-decoration: none;
        color: #007BFF;
    }

    .courses li a:hover {
        text-decoration: underline;
    }
    </style>
</head>
<body>
    <h1>Alumni Profiles and Skill Development</h1>
    <div id="profiles"></div>

    <script>
    // Inline JavaScript

    const profiles = [
        {
            name: 'Alex Miller',
            alumniJobs: ['Software Engineer at TechCorp', 'Backend Developer at CodeBase'],
            skills: ['Programming', 'Algorithms', 'Data Structures', 'Databases', 'APIs', 'Server-Side Development'],
            updatedSkills: [],
            recommendedCourses: []
        },
        {
            name: 'Bethany Green',
            alumniJobs: ['Data Scientist at DataX'],
            skills: ['Machine Learning', 'Statistics', 'Data Analysis'],
            updatedSkills: [],
            recommendedCourses: []
        },
        {
            name: 'Carl Edwards',
            alumniJobs: ['Product Manager at InnovateLtd'],
            skills: ['Leadership', 'Strategic Thinking', 'Communication'],
            updatedSkills: [],
            recommendedCourses: []
        },
        {
            name: 'Denise Brown',
            alumniJobs: ['UX Designer at DesignHub'],
            skills: ['User Research', 'Prototyping', 'Design Thinking'],
            updatedSkills: [],
            recommendedCourses: []
        },
        {
            name: 'Ethan Johnson',
            alumniJobs: ['Frontend Developer at WebWorks'],
            skills: ['HTML/CSS', 'JavaScript', 'Responsive Design'],
            updatedSkills: [],
            recommendedCourses: []
        }
    ];

    const skillCourses = {
        'Programming': [
            { name: 'Complete Python Bootcamp', url: 'https://www.udemy.com/course/complete-python-bootcamp/' }
        ],
        'Algorithms': [
            { name: 'Algorithms and Data Structures in Java', url: 'https://www.udemy.com/course/java-algorithms/' }
        ],
        'Data Structures': [
            { name: 'Mastering Data Structures', url: 'https://www.udemy.com/course/mastering-data-structures/' }
        ],
        'Databases': [
            { name: 'SQL for Data Analysis', url: 'https://www.udemy.com/course/sql-for-data-analysis/' }
        ],
        'APIs': [
            { name: 'REST API Development with Flask and Python', url: 'https://www.udemy.com/course/rest-api-flask-and-python/' }
        ],
        'Server-Side Development': [
            { name: 'Node.js Developer Course', url: 'https://www.udemy.com/course/the-complete-nodejs-developer-course-2/' }
        ],
        'Machine Learning': [
            { name: 'Machine Learning A-Z', url: 'https://www.udemy.com/course/machinelearning/' }
        ],
        'Statistics': [
            { name: 'Statistics for Data Science', url: 'https://www.udemy.com/course/statistics-data-science/' }
        ],
        'Data Analysis': [
            { name: 'Data Analysis with Pandas and Python', url: 'https://www.udemy.com/course/data-analysis-with-pandas/' }
        ],
        'Leadership': [
            { name: 'Leadership Mastery', url: 'https://www.udemy.com/course/leadership-mastery/' }
        ],
        'Strategic Thinking': [
            { name: 'Strategic Thinking Skills', url: 'https://www.udemy.com/course/strategic-thinking-skills/' }
        ],
        'Communication': [
            { name: 'Effective Communication Skills', url: 'https://www.udemy.com/course/communication-skills/' }
        ],
        'User Research': [
            { name: 'User Experience Design Essentials', url: 'https://www.udemy.com/course/ui-ux-web-design-using-adobe-xd/' }
        ],
        'Prototyping': [
            { name: 'UX & Web Design Master Course', url: 'https://www.udemy.com/course/ux-web-design-master-course-strategy-design-development/' }
        ],
        'Design Thinking': [
            { name: 'Design Thinking Guide for Successful Professionals', url: 'https://www.udemy.com/course/design-thinking-guide/' }
        ],
        'HTML/CSS': [
            { name: 'Modern HTML & CSS From The Beginning', url: 'https://www.udemy.com/course/modern-html-css-from-the-beginning/' }
        ],
        'JavaScript': [
            { name: 'The Complete JavaScript Course', url: 'https://www.udemy.com/course/the-complete-javascript-course/' }
        ],
        'Responsive Design': [
            { name: 'Responsive Web Design: HTML5 + CSS3 for Entrepreneurs', url: 'https://www.udemy.com/course/responsive-web-design/' }
        ]
    };

    function findCoursesForSkills(skills) {
        let courses = [];
        skills.forEach(skill => {
            if (skillCourses[skill]) {
                skillCourses[skill].forEach(course => {
                    courses.push({ ...course, skill: skill });
                });
            }
        });
        return courses;
    }

    function renderProfiles() {
        const profilesContainer = document.getElementById('profiles');

        profiles.forEach(profile => {
            profile.recommendedCourses = findCoursesForSkills(profile.skills);

            const profileDiv = document.createElement('div');
            profileDiv.className = 'profile';

            const nameHeading = document.createElement('h2');
            nameHeading.textContent = profile.name;
            profileDiv.appendChild(nameHeading);

            const jobsPara = document.createElement('p');
            jobsPara.textContent = `Alumni Jobs: ${profile.alumniJobs.join(', ')}`;
            profileDiv.appendChild(jobsPara);

            const skillsHeading = document.createElement('h3');
            skillsHeading.textContent = 'Skills:';
            profileDiv.appendChild(skillsHeading);

            const skillsList = document.createElement('ul');
            skillsList.className = 'skills';
            profile.skills.forEach(skill => {
                const skillItem = document.createElement('li');
                skillItem.textContent = skill;
                skillsList.appendChild(skillItem);
            });
            profileDiv.appendChild(skillsList);

            const coursesHeading = document.createElement('h3');
            coursesHeading.textContent = 'Recommended Courses:';
            profileDiv.appendChild(coursesHeading);

            const coursesList = document.createElement('ul');
            coursesList.className = 'courses';
            profile.recommendedCourses.forEach(course => {
                const courseItem = document.createElement('li');
                const courseLink = document.createElement('a');
                courseLink.href = course.url;
                courseLink.target = '_blank';
                courseLink.textContent = `${course.name} (Skill: ${course.skill})`;
                courseLink.addEventListener('click', () => {
                    updateProfileSkills(profile.name, course.skill);
                });
                courseItem.appendChild(courseLink);
                coursesList.appendChild(courseItem);
            });
            profileDiv.appendChild(coursesList);

            profilesContainer.appendChild(profileDiv);
        });
    }

    function updateProfileSkills(profileName, skill) {
        const profile = profiles.find(p => p.name === profileName);
        if (profile && !profile.updatedSkills.includes(skill)) {
            profile.updatedSkills.push(skill);
            alert(`Skill "${skill}" added to ${profile.name}'s profile.`);
            // Optionally, re-render the profile to update skills displayed
        }
    }

    document.addEventListener('DOMContentLoaded', renderProfiles);
    </script>
</body>
</html>
