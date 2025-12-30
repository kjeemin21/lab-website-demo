---
layout: default
title: Home
---

<section id="about" class="section">
    <div class="container">
        <h2>About</h2>
        <div class="content">
            <p>Welcome to {{ site.title }}. We are dedicated to advancing research in our field.</p>
            <!-- Add your lab description here -->
        </div>
    </div>
</section>

<section id="professor" class="section">
    <div class="container">
        <h2>Professor</h2>
        <div class="content">
            {% if site.data.professor %}
            <div class="professor-info">
                {% if site.data.professor.image %}
                <div class="professor-image">
                    <img src="{{ site.data.professor.image | relative_url }}" alt="{{ site.data.professor.name }}">
                </div>
                {% else %}
                <div class="professor-image">
                    <img src="{{ '/assets/images/icons/profile_icon.svg' | relative_url }}" alt="{{ site.data.professor.name }}">
                </div>
                {% endif %}
                <h3>{{ site.data.professor.name }}</h3>
                {% if site.data.professor.title %}
                <p class="title">{{ site.data.professor.title }}</p>
                {% endif %}
                {% if site.data.professor.email %}
                <p class="email">Email: <a href="mailto:{{ site.data.professor.email }}">{{ site.data.professor.email }}</a></p>
                {% endif %}
                {% if site.data.professor.bio %}
                <div class="bio">
                    {{ site.data.professor.bio | markdownify }}
                </div>
                {% endif %}
            </div>
            {% else %}
            <p>Professor information will be added here.</p>
            {% endif %}
        </div>
    </div>
</section>

<section id="members" class="section">
    <div class="container">
        <h2>Members</h2>
        <div class="content">
            {% if site.data.members %}
            <!-- Students Subsection -->
            {% assign students = site.data.members | where: "status", "Student" %}
            {% if students.size > 0 %}
            <div class="members-subsection">
                <h3 class="subsection-title">Students</h3>
                <div class="members-grid">
                    {% for member in students %}
                    <div class="member-card">
                        <div class="member-image">
                            {% if member.image %}
                            <img src="{{ member.image | relative_url }}" alt="{{ member.name }}">
                            {% else %}
                            <img src="{{ '/assets/images/icons/profile_icon.svg' | relative_url }}" alt="{{ member.name }}" class="default-icon">
                            {% endif %}
                        </div>
                        <div class="member-info">
                            <h3>{{ member.name }}</h3>
                            {% if member.role %}
                            <p class="role">{{ member.role }}</p>
                            {% endif %}
                            {% if member.email %}
                            <p class="email"><a href="mailto:{{ member.email }}">{{ member.email }}</a></p>
                            {% endif %}
                            {% if member.research %}
                            <p class="research">{{ member.research }}</p>
                            {% endif %}
                        </div>
                    </div>
                    {% endfor %}
                </div>
            </div>
            {% endif %}
            
            <!-- Alumni Subsection -->
            {% assign alumni = site.data.members | where: "status", "Alumni" %}
            {% if alumni.size > 0 %}
            <div class="members-subsection">
                <h3 class="subsection-title">Alumni</h3>
                <div class="members-grid">
                    {% for member in alumni %}
                    <div class="member-card">
                        <div class="member-image">
                            {% if member.image %}
                            <img src="{{ member.image | relative_url }}" alt="{{ member.name }}">
                            {% else %}
                            <img src="{{ '/assets/images/icons/profile_icon.svg' | relative_url }}" alt="{{ member.name }}" class="default-icon">
                            {% endif %}
                        </div>
                        <div class="member-info">
                            <h3>{{ member.name }}</h3>
                            {% if member.role %}
                            <p class="role">{{ member.role }}</p>
                            {% endif %}
                            {% if member.email %}
                            <p class="email"><a href="mailto:{{ member.email }}">{{ member.email }}</a></p>
                            {% endif %}
                            {% if member.research %}
                            <p class="research">{{ member.research }}</p>
                            {% endif %}
                            {% if member.graduation_year %}
                            <p class="graduation">Graduated: {{ member.graduation_year }}</p>
                            {% endif %}
                        </div>
                    </div>
                    {% endfor %}
                </div>
            </div>
            {% endif %}
            
            {% if students.size == 0 and alumni.size == 0 %}
            <p>Member information will be added here.</p>
            {% endif %}
            {% else %}
            <p>Member information will be added here.</p>
            {% endif %}
        </div>
    </div>
</section>

<section id="publications" class="section">
    <div class="container">
        <h2>Publications</h2>
        <div class="content">
            {% if site.data.publications %}
            <div class="publications-list">
                {% for pub in site.data.publications %}
                <div class="publication-item">
                    <h3>{{ pub.title }}</h3>
                    <p class="authors">{{ pub.authors }}</p>
                    {% if pub.venue %}
                    <p class="venue">{{ pub.venue }}</p>
                    {% endif %}
                    {% if pub.year %}
                    <p class="year">{{ pub.year }}</p>
                    {% endif %}
                    {% if pub.links %}
                    <div class="publication-links">
                        {% if pub.links.link %}
                        <a href="{{ pub.links.link }}" target="_blank" rel="noopener" class="pub-link" title="Link">
                            <img src="{{ '/assets/images/icons/link_icon.svg' | relative_url }}" alt="Link" class="link-icon">
                            <span>Link</span>
                        </a>
                        {% endif %}
                        {% if pub.links.paper %}
                        <a href="{{ pub.links.paper }}" target="_blank" rel="noopener" class="pub-link" title="Paper">
                            <img src="{{ '/assets/images/icons/paper_icon.svg' | relative_url }}" alt="Paper" class="link-icon">
                            <span>Paper</span>
                        </a>
                        {% endif %}
                        {% if pub.links.arxiv %}
                        <a href="{{ pub.links.arxiv }}" target="_blank" rel="noopener" class="pub-link" title="arXiv">
                            <img src="{{ '/assets/images/icons/arXiv_icon_temp.svg' | relative_url }}" alt="arXiv" class="link-icon">
                            <span>arXiv</span>
                        </a>
                        {% endif %}
                        {% if pub.links.bibtex %}
                        <a href="{{ pub.links.bibtex }}" target="_blank" rel="noopener" class="pub-link" title="BibTeX">
                            <img src="{{ '/assets/images/icons/bibtex_icon.svg' | relative_url }}" alt="BibTeX" class="link-icon">
                            <span>BibTeX</span>
                        </a>
                        {% endif %}
                        {% if pub.links.slides %}
                        <a href="{{ pub.links.slides }}" target="_blank" rel="noopener" class="pub-link" title="Slides">
                            <img src="{{ '/assets/images/icons/slides_icon.svg' | relative_url }}" alt="Slides" class="link-icon">
                            <span>Slides</span>
                        </a>
                        {% endif %}
                        {% if pub.links.poster %}
                        <a href="{{ pub.links.poster }}" target="_blank" rel="noopener" class="pub-link" title="Poster">
                            <img src="{{ '/assets/images/icons/poster_icon.svg' | relative_url }}" alt="Poster" class="link-icon">
                            <span>Poster</span>
                        </a>
                        {% endif %}
                        {% if pub.links.code %}
                        <a href="{{ pub.links.code }}" target="_blank" rel="noopener" class="pub-link" title="Code">
                            <img src="{{ '/assets/images/icons/code_icon.svg' | relative_url }}" alt="Code" class="link-icon">
                            <span>Code</span>
                        </a>
                        {% endif %}
                        {% if pub.links.video %}
                        <a href="{{ pub.links.video }}" target="_blank" rel="noopener" class="pub-link" title="Video">
                            <img src="{{ '/assets/images/icons/video_icon.svg' | relative_url }}" alt="Video" class="link-icon">
                            <span>Video</span>
                        </a>
                        {% endif %}
                    </div>
                    {% endif %}
                </div>
                {% endfor %}
            </div>
            {% else %}
            <p>Publications will be listed here.</p>
            {% endif %}
        </div>
    </div>
</section>

<section id="projects" class="section">
    <div class="container">
        <h2>Projects</h2>
        <div class="content">
            {% if site.data.projects %}
            <div class="projects-grid">
                {% for project in site.data.projects %}
                <div class="project-card">
                    <h3>{{ project.title }}</h3>
                    {% if project.description %}
                    <p>{{ project.description }}</p>
                    {% endif %}
                    {% if project.period %}
                    <p class="period">{{ project.period }}</p>
                    {% endif %}
                    {% if project.status %}
                    <span class="status status-{{ project.status | downcase }}">{{ project.status }}</span>
                    {% endif %}
                </div>
                {% endfor %}
            </div>
            {% else %}
            <p>Project information will be added here.</p>
            {% endif %}
        </div>
    </div>
</section>

<section id="photos" class="section">
    <div class="container">
        <h2>Photos</h2>
        <div class="content">
            {% if site.data.photos %}
            <div class="photos-grid">
                {% for photo in site.data.photos %}
                <div class="photo-item">
                    {% if photo.image %}
                    <img src="{{ photo.image | relative_url }}" alt="{{ photo.caption | default: 'Lab photo' }}">
                    {% endif %}
                    {% if photo.caption %}
                    <p class="caption">{{ photo.caption }}</p>
                    {% endif %}
                </div>
                {% endfor %}
            </div>
            {% else %}
            <p>Photos will be displayed here. Add images to the <code>assets/images/photos/</code> directory and update <code>_data/photos.yml</code>.</p>
            {% endif %}
        </div>
    </div>
</section>

<section id="contacts" class="section">
    <div class="container">
        <h2>Contacts</h2>
        <div class="content">
            <div class="contact-info">
                {% if site.email %}
                <p><strong>Email:</strong> <a href="mailto:{{ site.email }}">{{ site.email }}</a></p>
                {% endif %}
                {% if site.data.contacts %}
                    {% if site.data.contacts.address %}
                    <p><strong>Address:</strong> {{ site.data.contacts.address }}</p>
                    {% endif %}
                    {% if site.data.contacts.phone %}
                    <p><strong>Phone:</strong> {{ site.data.contacts.phone }}</p>
                    {% endif %}
                    {% if site.data.contacts.office %}
                    <p><strong>Office:</strong> {{ site.data.contacts.office }}</p>
                    {% endif %}
                {% endif %}
            </div>
        </div>
    </div>
</section>
