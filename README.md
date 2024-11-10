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
    <h1>Student Profiles and Skill Development</h1>
    <div id="profiles"></div>

    <script>
    // Inline JavaScript

    const profiles = [
        {
            name: 'Emily Zhang',
            university: 'University of California, Berkeley',
            subject: 'Software Engineering (1st Year)',
            skills: ['HTML', 'CSS', 'JavaScript (basic)', 'Teamwork'],
            interests: ['Web Development', 'User Experience Design'],
            updatedSkills: [],
            recommendedCourses: []
        },
        {
            name: 'Ryan Thompson',
            university: 'University of Toronto',
            subject: 'Environmental Science (2nd Year)',
            skills: ['Data Collection', 'GIS (beginner)', 'Research', 'Microsoft Excel'],
            interests: ['Sustainability', 'Conservation', 'Environmental Policy'],
            updatedSkills: [],
            recommendedCourses: []
        },
        {
            name: 'Mia Fernandez',
            university: 'New York University',
            subject: 'Marketing (3rd Year)',
            skills: ['Social Media Marketing', 'Content Creation', 'Google Analytics', 'Event Planning', 'Copywriting'],
            interests: ['Digital Marketing', 'Brand Strategy', 'Social Media Trends'],
            updatedSkills: [],
            recommendedCourses: []
        },
        {
            name: 'Thomas Patel',
            university: 'Georgia Institute of Technology',
            subject: 'Mechanical Engineering (Final Year)',
            skills: ['CAD (SolidWorks, AutoCAD)', '3D Modeling', 'MATLAB', 'Project Management', 'Lean Manufacturing'],
            interests: ['Automotive Design', 'Sustainable Manufacturing', 'Robotics'],
            updatedSkills: [],
            recommendedCourses: []
        },
        {
            name: 'Amina Khan',
            university: 'University of Oxford',
            subject: 'Data Science (Graduate Student)',
            skills: ['Python', 'SQL', 'Machine Learning', 'Data Visualization (Tableau, Power BI)', 'Data Analysis (R, Excel)'],
            interests: ['Predictive Analytics', 'Artificial Intelligence', 'Healthcare Data Science'],
            updatedSkills: [],
            recommendedCourses: []
        }
    ];

    const allSkills = [
        'HTML', 'CSS', 'JavaScript (basic)', 'JavaScript (advanced)', 'Teamwork', 'Git', 'React', 'Node.js', 'UI/UX Design',
        'Data Collection', 'GIS (advanced)', 'Data Analysis', 'Environmental Impact Assessment', 'Policy Writing',
        'SEO', 'Email Marketing', 'Adobe Photoshop', 'Adobe Illustrator',
        'Finite Element Analysis', 'Control Systems', 'Robotics Programming',
        'Deep Learning', 'Natural Language Processing', 'Big Data', 'Cloud Computing'
    ];

    const skillCourses = {
        'JavaScript (advanced)': [
            { name: 'The Complete JavaScript Course', url: 'https://www.udemy.com/course/the-complete-javascript-course/' }
        ],
        'Git': [
            { name: 'Git & GitHub Bootcamp', url: 'https://www.udemy.com/course/git-and-github-bootcamp/' }
        ],
        'React': [
            { name: 'React - The Complete Guide', url: 'https://www.udemy.com/course/react-the-complete-guide-incl-redux/' }
        ],
        'Node.js': [
            { name: 'The Complete Node.js Developer Course', url: 'https://www.udemy.com/course/the-complete-nodejs-developer-course-2/' }
        ],
        'UI/UX Design': [
            { name: 'User Experience Design Essentials', url: 'https://www.udemy.com/course/ui-ux-web-design-using-adobe-xd/' }
        ],
        'GIS (advanced)': [
            { name: 'Advanced GIS Techniques', url: 'https://www.udemy.com/course/advanced-gis-techniques/' }
        ],
        'Data Analysis': [
            { name: 'Data Analysis with Python and Pandas', url: 'https://www.udemy.com/course/data-analysis-with-pandas/' }
        ],
        'Environmental Impact Assessment': [
            { name: 'Environmental Impact Assessment Course', url: 'https://www.udemy.com/course/environmental-impact-assessment/' }
        ],
        'Policy Writing': [
            { name: 'Policy Writing Masterclass', url: 'https://www.udemy.com/course/policy-writing/' }
        ],
        'SEO': [
            { name: 'SEO Masterclass: Beginner to Advanced', url: 'https://www.udemy.com/course/seo-ultimate-guide/' }
        ],
        'Email Marketing': [
            { name: 'Email Marketing Basics', url: 'https://www.udemy.com/course/email-marketing-basics/' }
        ],
        'Adobe Photoshop': [
            { name: 'Adobe Photoshop CC – Essentials Training Course', url: 'https://www.udemy.com/course/adobe-photoshop-cc-essentials-training-course/' }
        ],
        'Adobe Illustrator': [
            { name: 'Adobe Illustrator CC – Essentials Training', url: 'https://www.udemy.com/course/adobe-illustrator-cc-essentials-training/' }
        ],
        'Finite Element Analysis': [
            { name: 'Finite Element Analysis for Mechanical Engineers', url: 'https://www.udemy.com/course/finite-element-analysis/' }
        ],
        'Control Systems': [
            { name: 'Control Systems Made Simple', url: 'https://www.udemy.com/course/control-systems/' }
        ],
        'Robotics Programming': [
            { name: 'Robotics: Learn by Building', url: 'https://www.udemy.com/course/robotics-learn-by-building/' }
        ],
        'Deep Learning': [
            { name: 'Deep Learning A-Z™', url: 'https://www.udemy.com/course/deeplearning/' }
        ],
        'Natural Language Processing': [
            { name: 'Natural Language Processing with Python', url: 'https://www.udemy.com/course/nlp-natural-language-processing-with-python/' }
        ],
        'Big Data': [
            { name: 'Big Data Basics', url: 'https://www.udemy.com/course/big-data-basics/' }
        ],
        'Cloud Computing': [
            { name: 'Cloud Computing Fundamentals', url: 'https://www.udemy.com/course/cloud-computing-fundamentals/' }
        ]
    };

    function findCoursesForMissingSkills(profile) {
        const existingSkills = profile.skills.map(skill => skill.toLowerCase());
        const missingSkills = allSkills.filter(skill => !existingSkills.includes(skill.toLowerCase()));
        let courses = [];
        missingSkills.forEach(skill => {
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
            // Find courses for missing skills
            profile.recommendedCourses = findCoursesForMissingSkills(profile);

            const profileDiv = document.createElement('div');
            profileDiv.className = 'profile';

            const nameHeading = document.createElement('h2');
            nameHeading.textContent = profile.name;
            profileDiv.appendChild(nameHeading);

            const uniPara = document.createElement('p');
            uniPara.textContent = `University: ${profile.university}`;
            profileDiv.appendChild(uniPara);

            const subjectPara = document.createElement('p');
            subjectPara.textContent = `Subject: ${profile.subject}`;
            profileDiv.appendChild(subjectPara);

            const skillsHeading = document.createElement('h3');
            skillsHeading.textContent = 'Current Skills:';
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
            coursesHeading.textContent = 'Recommended Courses for New Skills:';
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
        if (profile && !profile.skills.includes(skill)) {
            profile.skills.push(skill);
            alert(`Skill "${skill}" has been added to ${profile.name}'s profile.`);
            // Optionally, re-render the profile to update displayed skills and recommendations
            // For simplicity, we are not re-rendering in this example
        }
    }

    document.addEventListener('DOMContentLoaded', renderProfiles);
    </script>
</body>
</html>
