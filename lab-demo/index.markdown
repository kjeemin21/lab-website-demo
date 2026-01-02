---
layout: default
title: Home
---

<section id="about" class="section tab-panel active">
    <div class="container about-container">
        {% if site.data.about %}
        <div class="about-content">
            <!-- Hero Image Section -->
            <div class="about-hero">
                {% if site.data.about.hero_image %}
                <div class="about-hero-image">
                    <img src="{{ site.data.about.hero_image | relative_url }}" alt="{{ site.data.about.title }}">
                    <div class="about-hero-overlay">
                        <h1 class="about-hero-title">{{ site.data.about.title }}</h1>
                        {% if site.data.about.subtitle %}
                        <p class="about-hero-subtitle">{{ site.data.about.subtitle }}</p>
                        {% endif %}
                    </div>
                </div>
                {% endif %}
            </div>
            
            <!-- Description Section -->
            <div class="about-description">
                <div class="about-description-content">
                    {% if site.data.about.description %}
                    <p class="about-text">{{ site.data.about.description }}</p>
                    {% endif %}
                    
                    {% if site.data.about.mission %}
                    <div class="about-mission">
                        <h3 class="about-mission-title">Our Mission</h3>
                        <p class="about-mission-text">{{ site.data.about.mission }}</p>
                    </div>
                    {% endif %}
                </div>
            </div>
            
            <!-- Research Areas Section -->
            {% if site.data.about.research_areas %}
            <div class="about-research-areas">
                <h3 class="about-section-title">Research Areas</h3>
                <div class="research-areas-grid">
                    {% for area in site.data.about.research_areas %}
                    <div class="research-area-card">
                        <span class="research-area-icon">●</span>
                        <span class="research-area-name">{{ area }}</span>
                    </div>
                    {% endfor %}
                </div>
            </div>
            {% endif %}
        </div>
        {% else %}
        <div class="content">
            <h2>About</h2>
            <p>Welcome to {{ site.title }}. We are dedicated to advancing research in our field.</p>
        </div>
        {% endif %}
    </div>
</section>

<section id="professor" class="section tab-panel">
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
                
                <div class="professor-details">
                    {% if site.data.professor.title %}
                    <div class="detail-item">
                        <span class="detail-label">•</span>
                        <span class="detail-content">{{ site.data.professor.title }}</span>
                    </div>
                    {% endif %}
                    
                    {% if site.data.professor.adjunct_positions %}
                    {% for position in site.data.professor.adjunct_positions %}
                    <div class="detail-item detail-indent">
                        <span class="detail-label"></span>
                        <span class="detail-content">{{ position }}</span>
                    </div>
                    {% endfor %}
                    {% endif %}
                    
                    {% if site.data.professor.email %}
                    <div class="detail-item">
                        <span class="detail-label">•</span>
                        <span class="detail-content"><strong>Email:</strong> <a href="mailto:{{ site.data.professor.email }}">{{ site.data.professor.email }}</a></span>
                    </div>
                    {% endif %}
                    
                    {% if site.data.professor.office %}
                    <div class="detail-item">
                        <span class="detail-label">•</span>
                        <span class="detail-content"><strong>Office:</strong> {{ site.data.professor.office }}</span>
                    </div>
                    {% endif %}
                    
                    {% if site.data.professor.education %}
                    <div class="detail-item">
                        <span class="detail-label">•</span>
                        <span class="detail-content">Education</span>
                    </div>
                    <div class="detail-item detail-indent">
                        <span class="detail-label"></span>
                        <span class="detail-content">
                            {{ site.data.professor.education.degree }}, {{ site.data.professor.education.university }}, {{ site.data.professor.education.year }}.
                        </span>
                    </div>
                    {% if site.data.professor.education.supervisor %}
                    <div class="detail-item detail-indent">
                        <span class="detail-label"></span>
                        <span class="detail-content">
                            (Supervisor: {% if site.data.professor.education.supervisor_link %}<a href="{{ site.data.professor.education.supervisor_link }}" target="_blank" rel="noopener">{{ site.data.professor.education.supervisor }}</a>{% else %}{{ site.data.professor.education.supervisor }}{% endif %})
                        </span>
                    </div>
                    {% endif %}
                    {% endif %}
                    
                    {% if site.data.professor.research_interests %}
                    <div class="detail-item">
                        <span class="detail-label">•</span>
                        <span class="detail-content">Research Interests</span>
                    </div>
                    <div class="detail-item detail-indent">
                        <span class="detail-label"></span>
                        <span class="detail-content">{{ site.data.professor.research_interests }}</span>
                    </div>
                    {% endif %}
                    
                    {% if site.data.professor.cv_link %}
                    <div class="detail-item">
                        <span class="detail-label"></span>
                        <span class="detail-content">
                            <a href="{{ site.data.professor.cv_link | relative_url }}" target="_blank" rel="noopener" class="cv-link">Curriculum Vitae</a>
                        </span>
                    </div>
                    {% endif %}
                </div>
            </div>
            {% else %}
            <p>Professor information will be added here.</p>
            {% endif %}
        </div>
    </div>
</section>

<section id="members" class="section tab-panel">
    <div class="container">
        <div class="members-header">
            <h2>Members</h2>
            <button class="members-menu-toggle" aria-label="Toggle members menu">
                <img src="{{ '/assets/images/icons/menu_icon.svg' | relative_url }}" alt="Menu" class="menu-icon">
            </button>
        </div>
        <div class="content">
            {% if site.data.members %}
            <div class="members-container">
                <div class="members-list">
                    {% assign students = site.data.members | where: "status", "Student" %}
                    {% assign phd_students = students | where: "role", "Ph.D. Student" %}
                    {% assign ms_students = students | where: "role", "Master's Student" %}
                    {% assign alumni = site.data.members | where: "status", "Alumni" %}
                    
                    <!-- Students Category -->
                    <div class="member-category" data-category="students">
                        <!-- Ph.D Students Subsection -->
                        {% if phd_students.size > 0 %}
                        <div class="members-subsection">
                            <h3 class="subsection-title">Ph.D Students</h3>
                            <div class="members-grid">
                                {% for member in phd_students %}
                                <div class="member-card">
                                    <div class="member-links-top">
                                        {% if member.homepage_url %}
                                        <a href="{{ member.homepage_url }}" target="_blank" rel="noopener" class="member-link" title="Homepage">
                                            <img src="{{ '/assets/images/icons/homepage_icon.svg' | relative_url }}" alt="Homepage" class="link-icon">
                                        </a>
                                        {% endif %}
                                        {% if member.scholar_url %}
                                        <a href="{{ member.scholar_url }}" target="_blank" rel="noopener" class="member-link" title="Google Scholar">
                                            <img src="{{ '/assets/images/icons/scholar_icon.svg' | relative_url }}" alt="Google Scholar" class="link-icon">
                                        </a>
                                        {% endif %}
                                    </div>
                                    <div class="member-image">
                                        {% if member.image %}
                                        <img src="{{ member.image | relative_url }}" alt="{{ member.name }}">
                                        {% else %}
                                        <img src="{{ '/assets/images/icons/profile_icon.svg' | relative_url }}" alt="{{ member.name }}" class="default-icon">
                                        {% endif %}
                                    </div>
                                    <div class="member-info">
                                        <div class="member-header">
                                            <h3 class="member-name">{{ member.name }}</h3>
                                        </div>
                                        {% if member.email %}
                                        <p class="email"><a href="mailto:{{ member.email }}">{{ member.email }}</a></p>
                                        {% endif %}
                                        {% if member.research %}
                                        <p class="research">{{ member.research }}</p>
                                        {% endif %}
                                        {% if member.education_history %}
                                        <div class="education-history">
                                            {% for edu in member.education_history %}
                                            <p class="education-item">
                                                <span class="education-period">{{ edu.period }}:</span>
                                                <span class="education-description">{{ edu.description }}</span>
                                            </p>
                                            {% endfor %}
                                        </div>
                                        {% endif %}
                                    </div>
                                </div>
                                {% endfor %}
                            </div>
                        </div>
                        {% endif %}
                        
                        <!-- M.S. Students Subsection -->
                        {% if ms_students.size > 0 %}
                        <div class="members-subsection">
                            <h3 class="subsection-title">M.S. Students</h3>
                            <div class="members-grid">
                                {% for member in ms_students %}
                                <div class="member-card">
                                    <div class="member-links-top">
                                        {% if member.homepage_url %}
                                        <a href="{{ member.homepage_url }}" target="_blank" rel="noopener" class="member-link" title="Homepage">
                                            <img src="{{ '/assets/images/icons/homepage_icon.svg' | relative_url }}" alt="Homepage" class="link-icon">
                                        </a>
                                        {% endif %}
                                        {% if member.scholar_url %}
                                        <a href="{{ member.scholar_url }}" target="_blank" rel="noopener" class="member-link" title="Google Scholar">
                                            <img src="{{ '/assets/images/icons/scholar_icon.svg' | relative_url }}" alt="Google Scholar" class="link-icon">
                                        </a>
                                        {% endif %}
                                    </div>
                                    <div class="member-image">
                                        {% if member.image %}
                                        <img src="{{ member.image | relative_url }}" alt="{{ member.name }}">
                                        {% else %}
                                        <img src="{{ '/assets/images/icons/profile_icon.svg' | relative_url }}" alt="{{ member.name }}" class="default-icon">
                                        {% endif %}
                                    </div>
                                    <div class="member-info">
                                        <div class="member-header">
                                            <h3 class="member-name">{{ member.name }}</h3>
                                        </div>
                                        {% if member.email %}
                                        <p class="email"><a href="mailto:{{ member.email }}">{{ member.email }}</a></p>
                                        {% endif %}
                                        {% if member.research %}
                                        <p class="research">{{ member.research }}</p>
                                        {% endif %}
                                        {% if member.education_history %}
                                        <div class="education-history">
                                            {% for edu in member.education_history %}
                                            <p class="education-item">
                                                <span class="education-period">{{ edu.period }}:</span>
                                                <span class="education-description">{{ edu.description }}</span>
                                            </p>
                                            {% endfor %}
                                        </div>
                                        {% endif %}
                                    </div>
                                </div>
                                {% endfor %}
                            </div>
                        </div>
                        {% endif %}
                    </div>
                    
                    <!-- Alumni Category -->
                    <div class="member-category" data-category="alumni" style="display: none;">
                        {% if alumni.size > 0 %}
                        <div class="members-subsection">
                            <h3 class="subsection-title">Alumni</h3>
                            <div class="members-grid">
                                {% for member in alumni %}
                                <div class="member-card alumni-card">
                                    <div class="member-links-top">
                                        {% if member.homepage_url %}
                                        <a href="{{ member.homepage_url }}" target="_blank" rel="noopener" class="member-link" title="Homepage">
                                            <img src="{{ '/assets/images/icons/homepage_icon.svg' | relative_url }}" alt="Homepage" class="link-icon">
                                        </a>
                                        {% endif %}
                                        {% if member.scholar_url %}
                                        <a href="{{ member.scholar_url }}" target="_blank" rel="noopener" class="member-link" title="Google Scholar">
                                            <img src="{{ '/assets/images/icons/scholar_icon.svg' | relative_url }}" alt="Google Scholar" class="link-icon">
                                        </a>
                                        {% endif %}
                                    </div>
                                    <div class="member-image">
                                        {% if member.image %}
                                        <img src="{{ member.image | relative_url }}" alt="{{ member.name }}">
                                        {% else %}
                                        <img src="{{ '/assets/images/icons/profile_icon.svg' | relative_url }}" alt="{{ member.name }}" class="default-icon">
                                        {% endif %}
                                    </div>
                                    <div class="member-info">
                                        <div class="member-header">
                                            <h3 class="member-name">{{ member.name }}</h3>
                                        </div>
                                        {% if member.degree and member.graduation_date %}
                                        <p class="alumni-degree">{{ member.degree }}{% if member.graduation_date %}, {{ member.graduation_date }}{% endif %}{% if member.institution %}, {{ member.institution }}{% endif %}</p>
                                        {% endif %}
                                        {% if member.thesis %}
                                        <div class="thesis-info">
                                            <p class="thesis-title">
                                                <span class="thesis-label">Thesis:</span>
                                                {% if member.thesis.url and member.thesis.url != "" %}
                                                <a href="{{ member.thesis.url }}" target="_blank" rel="noopener">{{ member.thesis.title }}</a>
                                                {% else %}
                                                {{ member.thesis.title }}
                                                {% endif %}
                                            </p>
                                        </div>
                                        {% endif %}
                                        {% if member.education_history %}
                                        <div class="education-history">
                                            {% for edu in member.education_history %}
                                            <p class="education-item">
                                                <span class="education-period">{{ edu.period }}:</span>
                                                <span class="education-description">{{ edu.description }}</span>
                                            </p>
                                            {% endfor %}
                                        </div>
                                        {% endif %}
                                    </div>
                                </div>
                                {% endfor %}
                            </div>
                        </div>
                        {% endif %}
                    </div>
                </div>
            </div>
            
            <!-- Members Side Menu Overlay -->
            <div class="members-menu-overlay"></div>
            
            <nav class="members-side-menu">
                <div class="members-menu-header">
                    <button class="members-menu-close" aria-label="Close menu">
                        <span>&times;</span>
                    </button>
                </div>
                <ul class="members-menu-list">
                    <li><button class="member-menu-btn active" data-category="students">Students</button></li>
                    <li><button class="member-menu-btn" data-category="alumni">Alumni</button></li>
                </ul>
            </nav>
            {% else %}
            <p>Member information will be added here.</p>
            {% endif %}
        </div>
    </div>
</section>

<section id="publications" class="section tab-panel">
    <div class="container">
        <div class="publications-header">
            <h2>Publications</h2>
            <button class="publications-menu-toggle" aria-label="Toggle publications menu">
                <img src="{{ '/assets/images/icons/menu_icon.svg' | relative_url }}" alt="Menu" class="menu-icon">
            </button>
        </div>
        <div class="content">
            {% if site.data.publications %}
            <div class="publications-container">
                <div class="publications-list">
                    {% assign international_pubs = site.data.publications | where: "type", "international" %}
                    {% assign domestic_pubs = site.data.publications | where: "type", "domestic" %}
                    {% assign default_pubs = site.data.publications | where_exp: "pub", "pub.type == nil or pub.type == ''" %}
                    
                    <div class="publication-category" data-category="international">
                        {% for pub in site.data.publications %}
                        {% assign pub_type = pub.type | default: "international" %}
                        {% if pub_type == "international" %}
                        <div class="publication-item" data-year="{{ pub.year }}" data-title="{{ pub.title | downcase }}" data-type="{{ pub_type }}">
                            {% if pub.year %}
                            <span class="year-badge">{{ pub.year }}</span>
                            {% endif %}
                            <h3>{{ pub.title }}</h3>
                            <p class="authors">{{ pub.authors | replace: "‡", "<sup>‡</sup>" }}</p>
                            {% if pub.venue %}
                            <p class="venue">{{ pub.venue }}</p>
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
                                {% if pub.links.youtube %}
                                <a href="{{ pub.links.youtube }}" target="_blank" rel="noopener" class="pub-link" title="YouTube">
                                    <img src="{{ '/assets/images/icons/video_icon.svg' | relative_url }}" alt="YouTube" class="link-icon">
                                    <span>YouTube</span>
                                </a>
                                {% endif %}
                                {% if pub.links.promo %}
                                <a href="{{ pub.links.promo }}" target="_blank" rel="noopener" class="pub-link" title="Promo">
                                    <img src="{{ '/assets/images/icons/video_icon.svg' | relative_url }}" alt="Promo" class="link-icon">
                                    <span>Promo</span>
                                </a>
                                {% endif %}
                            </div>
                            {% endif %}
                        </div>
                        {% endif %}
                        {% endfor %}
                    </div>
                    
                    <div class="publication-category" data-category="domestic" style="display: none;">
                        {% for pub in site.data.publications %}
                        {% assign pub_type = pub.type | default: "international" %}
                        {% if pub_type == "domestic" %}
                        <div class="publication-item" data-year="{{ pub.year }}" data-title="{{ pub.title | downcase }}" data-type="{{ pub_type }}">
                            {% if pub.year %}
                            <span class="year-badge">{{ pub.year }}</span>
                            {% endif %}
                            <h3>{{ pub.title }}</h3>
                            <p class="authors">{{ pub.authors | replace: "‡", "<sup>‡</sup>" }}</p>
                            {% if pub.venue %}
                            <p class="venue">{{ pub.venue }}</p>
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
                                {% if pub.links.youtube %}
                                <a href="{{ pub.links.youtube }}" target="_blank" rel="noopener" class="pub-link" title="YouTube">
                                    <img src="{{ '/assets/images/icons/video_icon.svg' | relative_url }}" alt="YouTube" class="link-icon">
                                    <span>YouTube</span>
                                </a>
                                {% endif %}
                                {% if pub.links.promo %}
                                <a href="{{ pub.links.promo }}" target="_blank" rel="noopener" class="pub-link" title="Promo">
                                    <img src="{{ '/assets/images/icons/video_icon.svg' | relative_url }}" alt="Promo" class="link-icon">
                                    <span>Promo</span>
                                </a>
                                {% endif %}
                            </div>
                            {% endif %}
                        </div>
                        {% endif %}
                        {% endfor %}
                    </div>
                </div>
            </div>
            
            <!-- Publications Side Menu Overlay -->
            <div class="publications-menu-overlay"></div>
            
            <nav class="publications-side-menu">
                <div class="publications-menu-header">
                    <button class="publications-menu-close" aria-label="Close menu">
                        <span>&times;</span>
                    </button>
                </div>
                <ul class="publications-menu-list">
                    <li><button class="publication-menu-btn active" data-category="international">International</button></li>
                    <li><button class="publication-menu-btn" data-category="domestic">Domestic</button></li>
                </ul>
            </nav>
            {% else %}
            <p>Publications will be listed here.</p>
            {% endif %}
        </div>
    </div>
</section>

<section id="projects" class="section tab-panel">
    <div class="container">
        <h2>Projects</h2>
        <div class="content">
            {% if site.data.projects %}
            <div class="projects-list">
                {% for org in site.data.projects %}
                <div class="organization-card">
                    {% if org.logo %}
                    <div class="organization-logo">
                        <img src="{{ org.logo | relative_url }}" alt="{{ org.organization }}">
                    </div>
                    {% endif %}
                    <div class="organization-content">
                        <h3 class="organization-name">{{ org.organization }}</h3>
                        {% if org.projects %}
                        <ul class="projects-list-items">
                            {% for project in org.projects %}
                            <li class="project-item">
                                <span class="project-bullet">▶</span>
                                <div class="project-content">
                                    <div class="project-title">{{ project.title }}</div>
                                    <div class="project-meta">
                                        <span class="project-period">{{ project.period }}</span>
                                        {% if project.role %}
                                        <span class="project-role">{{ project.role }}</span>
                                        {% endif %}
                                    </div>
                                </div>
                            </li>
                            {% endfor %}
                        </ul>
                        {% endif %}
                    </div>
                </div>
                {% endfor %}
            </div>
            {% else %}
            <p>Project information will be added here.</p>
            {% endif %}
        </div>
    </div>
</section>

<section id="photos" class="section tab-panel">
    <div class="container">
        <h2>Photos</h2>
        <div class="content">
            {% if site.data.photos %}
            <div class="photos-grid">
                {% for photo in site.data.photos %}
                <div class="photo-item" data-image="{{ photo.image | relative_url }}">
                    {% if photo.image %}
                    <img src="{{ photo.image | relative_url }}" alt="{{ photo.caption | default: 'Lab photo' }}">
                    {% endif %}
                </div>
                {% endfor %}
            </div>
            
            <!-- Photo Pagination -->
            <div class="photo-pagination" id="photoPagination">
                <button class="pagination-btn pagination-prev" id="photoPrevBtn" aria-label="Previous page">
                    <span>&laquo;</span>
                </button>
                <div class="pagination-numbers" id="photoPaginationNumbers"></div>
                <button class="pagination-btn pagination-next" id="photoNextBtn" aria-label="Next page">
                    <span>&raquo;</span>
                </button>
            </div>
            
            <!-- Photo Lightbox -->
            <div class="photo-lightbox" id="photoLightbox">
                <button class="photo-lightbox-close" aria-label="Close lightbox">
                    <span>&times;</span>
                </button>
                <div class="photo-lightbox-content">
                    <img id="lightboxImage" src="" alt="Large photo">
                </div>
            </div>
            {% else %}
            <p>Photos will be displayed here. Add images to the <code>assets/images/photos/</code> directory and update <code>_data/photos.yml</code>.</p>
            {% endif %}
        </div>
    </div>
</section>

<section id="contacts" class="section tab-panel">
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
