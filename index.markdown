---
layout: default
title: Home
---

<section id="about" class="section tab-panel active">
    <div class="container about-container">
        {% if site.data.about %}
        <div class="about-content">
            <!-- Main Content: Image (Left) + Text (Right) -->
            <div class="about-main-section">
                <!-- Left: Hero Image -->
                <div class="about-main-image">
                    {% if site.data.about.hero_image %}
                    <img src="{{ site.data.about.hero_image | relative_url }}" alt="{{ site.data.about.title }}">
                    {% endif %}
                </div>
                
                <!-- Right: Description -->
                <div class="about-main-text">
                    {% if site.data.about.description %}
                    <p class="about-text">{{ site.data.about.description }}</p>
                    {% endif %}
                </div>
            </div>
            
            <!-- Research Areas Section (Below) -->
            {% if site.data.about.research_areas %}
            <div class="about-research-section">
                <h3 class="research-section-title">Research Areas</h3>
                <div class="research-tags-list">
                    {% for area in site.data.about.research_areas %}
                    <span class="research-tag" data-description="{{ area.description }}">{{ area.name }}</span>
                    {% endfor %}
                </div>
                
                <!-- Research Detail Panel -->
                <div class="research-detail-panel">
                    <h3 class="detail-title">연구 영역 상세</h3>
                    <p class="detail-content">연구 영역을 선택하면 자세한 내용이 표시됩니다.</p>
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
                </div>
                
                {% if site.data.professor.cv_link %}
                <a href="{{ site.data.professor.cv_link | relative_url }}" target="_blank" rel="noopener" class="cv-link">Curriculum Vitae</a>
                {% endif %}
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
                    
                    <!-- Ph.D Students Subsection -->
                    {% if phd_students.size > 0 %}
                    <div class="members-subsection" id="members-phd">
                        <h3 class="subsection-title">Ph.D. Students</h3>
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
                    <div class="members-subsection" id="members-ms">
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
                    
                    <!-- Alumni Subsection -->
                    {% if alumni.size > 0 %}
                    <div class="members-subsection" id="members-alumni">
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
            
            <!-- Members Side Menu Overlay -->
            <div class="members-menu-overlay"></div>
            
            <nav class="members-side-menu">
                <h3 class="members-menu-title">
                    Members
                    <button class="members-menu-close" aria-label="Close menu">
                        <span>&times;</span>
                    </button>
                </h3>
                <ul class="members-menu-list">
                    <li><button class="member-menu-btn active" data-scroll="members-phd">Ph.D. Students</button></li>
                    <li><button class="member-menu-btn" data-scroll="members-ms">M.S. Students</button></li>
                    <li><button class="member-menu-btn" data-scroll="members-alumni">Alumni</button></li>
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
                    {% assign domestic_pubs = site.data.publications | where: "type", "domestic" %}
                    {% assign all_pubs = site.data.publications %}
                    {% assign has_international = false %}
                    {% for pub in all_pubs %}
                        {% assign pub_type = pub.type | default: "international" %}
                        {% if pub_type != "domestic" and pub_type != "patent" %}
                            {% assign has_international = true %}
                        {% endif %}
                    {% endfor %}
                    
                    <!-- International Publications Section -->
                    {% if has_international %}
                    <div class="publications-section" id="publications-international">
                        <div style="display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 30px; padding-bottom: 15px; border-bottom: 2px solid var(--border-color);">
                            <h3 class="subsection-title" style="margin: 0; border: none; padding: 0;">International</h3>
                            <p style="font-size: 0.85rem; color: #666; margin: 0; font-style: italic;">‡: Equal Contribution, *: Corresponding Author</p>
                        </div>
                        {% assign int_count = 0 %}
                        {% for pub in site.data.publications %}
                        {% assign pub_type = pub.type | default: "international" %}
                        {% if pub_type != "domestic" and pub_type != "patent" %}
                        {% assign int_count = int_count | plus: 1 %}
                        <div class="publication-item {% if int_count > 10 %}publication-item-hidden{% endif %}" data-year="{{ pub.year }}" data-title="{{ pub.title | downcase }}" data-type="{{ pub_type }}">
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
                        {% if int_count > 10 %}
                        <div class="publications-show-more-container">
                            <button class="publications-show-more-btn" data-section="publications-international" data-limit="10">
                                <img src="{{ '/assets/images/icons/arrow_down_icon.svg' | relative_url }}" alt="Show More" class="show-more-icon">
                            </button>
                            <button class="publications-show-less-btn" data-section="publications-international" data-limit="10" style="display: none;">
                                <img src="{{ '/assets/images/icons/arrow_up_icon.svg' | relative_url }}" alt="Show Less" class="show-less-icon">
                            </button>
                        </div>
                        {% endif %}
                    </div>
                    {% endif %}
                    
                    <!-- Domestic Publications Section -->
                    {% if domestic_pubs.size > 0 %}
                    <div class="publications-section" id="publications-domestic">
                        <h3 class="subsection-title">Domestic</h3>
                        {% assign dom_count = 0 %}
                        {% for pub in site.data.publications %}
                        {% assign pub_type = pub.type | default: "international" %}
                        {% if pub_type == "domestic" %}
                        {% assign dom_count = dom_count | plus: 1 %}
                        <div class="publication-item {% if dom_count > 10 %}publication-item-hidden{% endif %}" data-year="{{ pub.year }}" data-title="{{ pub.title | downcase }}" data-type="{{ pub_type }}">
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
                        {% if dom_count > 10 %}
                        <div class="publications-show-more-container">
                            <button class="publications-show-more-btn" data-section="publications-domestic" data-limit="10">
                                <img src="{{ '/assets/images/icons/arrow_down_icon.svg' | relative_url }}" alt="Show More" class="show-more-icon">
                            </button>
                            <button class="publications-show-less-btn" data-section="publications-domestic" data-limit="10" style="display: none;">
                                <img src="{{ '/assets/images/icons/arrow_up_icon.svg' | relative_url }}" alt="Show Less" class="show-less-icon">
                            </button>
                        </div>
                        {% endif %}
                    </div>
                    {% endif %}
                    
                    <!-- Patents Section -->
                    {% assign patent_pubs = site.data.publications | where: "type", "patent" %}
                    {% if patent_pubs.size > 0 %}
                    <div class="publications-section" id="publications-patents">
                        <h3 class="subsection-title">Patents</h3>
                        {% assign patent_count = 0 %}
                        {% for pub in site.data.publications %}
                        {% assign pub_type = pub.type | default: "international" %}
                        {% if pub_type == "patent" %}
                        {% assign patent_count = patent_count | plus: 1 %}
                        <div class="publication-item {% if patent_count > 10 %}publication-item-hidden{% endif %}" data-year="{{ pub.year }}" data-title="{{ pub.title | downcase }}" data-type="{{ pub_type }}">
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
                            </div>
                            {% endif %}
                        </div>
                        {% endif %}
                        {% endfor %}
                        {% if patent_count > 10 %}
                        <div class="publications-show-more-container">
                            <button class="publications-show-more-btn" data-section="publications-patents" data-limit="10">
                                <img src="{{ '/assets/images/icons/arrow_down_icon.svg' | relative_url }}" alt="Show More" class="show-more-icon">
                            </button>
                            <button class="publications-show-less-btn" data-section="publications-patents" data-limit="10" style="display: none;">
                                <img src="{{ '/assets/images/icons/arrow_up_icon.svg' | relative_url }}" alt="Show Less" class="show-less-icon">
                            </button>
                        </div>
                        {% endif %}
                    </div>
                    {% endif %}
                </div>
            </div>
            
            <!-- Publications Side Menu Overlay -->
            <div class="publications-menu-overlay"></div>
            
            <nav class="publications-side-menu">
                <h3 class="publications-menu-title">
                    Publications
                    <button class="publications-menu-close" aria-label="Close menu">
                        <span>&times;</span>
                    </button>
                </h3>
                <ul class="publications-menu-list">
                    <li><button class="publication-menu-btn active" data-scroll="publications-international">International</button></li>
                    <li><button class="publication-menu-btn" data-scroll="publications-domestic">Domestic</button></li>
                    <li><button class="publication-menu-btn" data-scroll="publications-patents">Patents</button></li>
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
            <div class="photos-grid" id="photosGrid">
                <!-- Photos will be dynamically loaded here -->
            </div>
            
            <!-- Hidden data for JavaScript -->
            <script id="photos-data" type="application/json">
            [
            {% for photo in site.data.photos %}
            {
                "image": "{{ photo.image | relative_url }}",
                "caption": "{{ photo.caption | default: 'Lab photo' }}",
                "date": "{{ photo.date }}"
            }{% unless forloop.last %},{% endunless %}
            {% endfor %}
            ]
            </script>
            
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

<section id="recruit" class="section tab-panel">
    <div class="container">
        <h2>Recruit</h2>
        <div class="content">
            <!-- Recruitment Information -->
            <div class="recruitment-section">
                <div class="recruitment-links">
                    <a href="https://www.youtube.com/watch?v=dGNjNBvxrDA&t=1s&ab_channel=BDILab" target="_blank" rel="noopener" class="recruitment-link-btn">연구실 동영상</a>
                    <a href="/down/BDI_Lab_KAIST.pdf" target="_blank" rel="noopener" class="recruitment-link-btn">소개자료</a>
                    <a href="/down/BDI_Lab_video.html" target="_blank" rel="noopener" class="recruitment-link-btn">설명자료</a>
                    <a href="https://github.com/bdi-lab" target="_blank" rel="noopener" class="recruitment-link-btn">Github</a>
                    <a href="https://www.youtube.com/@bdi-lab" target="_blank" rel="noopener" class="recruitment-link-btn">YouTube</a>
                </div>
                <div class="recruitment-applications">
                    <p class="recruitment-title">[학생 모집 중]</p>
                    <p class="recruitment-item">
                        <strong>석사 신입생:</strong>
                        <a href="https://forms.gle/8TUm8iPkgvRQSZv89" target="_blank" rel="noopener" class="recruitment-link">지원서 링크</a>
                    </p>
                    <p class="recruitment-item">
                        <strong>학부 연구생:</strong>
                        <a href="https://forms.gle/vPZs2LjWPCJFCa4Z8" target="_blank" rel="noopener" class="recruitment-link">지원 링크</a>
                    </p>
                    <p class="recruitment-contact">
                        우리 연구실에 관심있는 학생들은 <a href="mailto:jjwhang@kaist.ac.kr" class="recruitment-link">jjwhang@kaist.ac.kr</a> 로 문의바랍니다.
                    </p>
                </div>
            </div>
            
            {% if site.data.recruit %}
            <div class="recruit-grid">
                <!-- Location Card -->
                {% if site.data.recruit.location %}
                <div class="recruit-card">
                    <h3 class="recruit-card-title">Location</h3>
                    <div class="recruit-card-content">
                        {% if site.data.recruit.location.building %}
                        <p class="recruit-item">{{ site.data.recruit.location.building }}</p>
                        {% endif %}
                        {% if site.data.recruit.location.professor_room %}
                        <p class="recruit-item"><strong>Prof.:</strong> {{ site.data.recruit.location.professor_room }}</p>
                        {% endif %}
                        {% if site.data.recruit.location.lab_room %}
                        <p class="recruit-item"><strong>Lab.:</strong> {{ site.data.recruit.location.lab_room }}</p>
                        {% endif %}
                        {% if site.data.recruit.location.admin_room %}
                        <p class="recruit-item"><strong>Admin.:</strong> {{ site.data.recruit.location.admin_room }}</p>
                        {% endif %}
                    </div>
                </div>
                {% endif %}
                
                <!-- Email Card -->
                {% if site.data.recruit.email %}
                <div class="recruit-card">
                    <h3 class="recruit-card-title">Email</h3>
                    <div class="recruit-card-content">
                        {% if site.data.recruit.email.professor_name %}
                        <p class="recruit-item">{{ site.data.recruit.email.professor_name }}</p>
                        {% endif %}
                        {% if site.data.recruit.email.professor_email %}
                        <p class="recruit-item">
                            <a href="mailto:{{ site.data.recruit.email.professor_email }}" class="recruit-link">
                                {{ site.data.recruit.email.professor_email }}
                            </a>
                        </p>
                        {% endif %}
                    </div>
                </div>
                {% endif %}
                
                <!-- Phone Card -->
                {% if site.data.recruit.phone %}
                <div class="recruit-card">
                    <h3 class="recruit-card-title">Tel</h3>
                    <div class="recruit-card-content">
                        {% if site.data.recruit.phone.professor %}
                        <p class="recruit-item"><strong>Prof.:</strong> {{ site.data.recruit.phone.professor }}</p>
                        {% endif %}
                        {% if site.data.recruit.phone.lab %}
                        <p class="recruit-item"><strong>Lab.:</strong> {{ site.data.recruit.phone.lab }}</p>
                        {% endif %}
                        {% if site.data.recruit.phone.admin %}
                        <p class="recruit-item"><strong>Admin.:</strong> {{ site.data.recruit.phone.admin }}</p>
                        {% endif %}
                    </div>
                </div>
                {% endif %}
            </div>
            {% else %}
            <div class="recruit-info">
                <p>Recruit information will be added here.</p>
            </div>
            {% endif %}
        </div>
    </div>
</section>

