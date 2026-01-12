# bdi-lab Demo Website

연구실 웹사이트를 위한 Jekyll 기반 정적 사이트입니다. GitHub Pages를 통해 배포됩니다.

## 🌐 배포된 사이트

- **URL**: [https://kjeemin21.github.io/lab-website-demo](https://kjeemin21.github.io/lab-website-demo)

## 📋 프로젝트 구조

```
lab-website-demo/
├── _config.yml          # Jekyll 설정 파일
├── _data/               # 데이터 파일 (YAML)
│   ├── about.yml        # 연구실 소개
│   ├── members.yml      # 멤버 정보
│   ├── photos.yml       # 사진 갤러리
│   ├── professor.yml    # 교수 정보
│   ├── projects.yml     # 프로젝트 정보
│   ├── publications.yml # 논문 목록
│   └── recruit.yml      # 채용 및 연락처 정보
├── _includes/           # 재사용 가능한 HTML 컴포넌트
│   ├── header.html
│   ├── footer.html
│   ├── side-menu.html
│   └── ...
├── _layouts/            # 레이아웃 템플릿
│   ├── default.html
│   └── 404.html
├── _posts/              # 블로그 포스트
├── _sass/               # SCSS 모듈 파일
│   ├── _variables.scss
│   ├── _base.scss
│   ├── _header.scss
│   ├── _about.scss
│   ├── _members.scss
│   └── ...
├── assets/              # 정적 자원
│   ├── css/
│   │   └── style.scss   # 메인 스타일시트 (SCSS)
│   ├── images/          # 이미지 파일
│   ├── down/            # 동영상, zip 파일 등
│   ├── pdf/             # PDF 파일 (Publications)
│   └── txt/             # Bibtex 파일 (Publications)
├── Gemfile              # Ruby gem 의존성
└── index.markdown       # 메인 페이지
```

## 🚀 로컬 개발 환경 설정

### 사전 요구사항

- Ruby 2.7.0 이상
- Bundler

### 설치 및 실행

1. **저장소 클론**
   ```bash
   git clone https://github.com/kjeemin21/lab-website-demo.git
   cd lab-website-demo
   ```

2. **의존성 설치**
   ```bash
   bundle install
   ```

3. **로컬 서버 실행**
   ```bash
   bundle exec jekyll serve
   ```

4. **브라우저에서 확인**
   
   브라우저에서 `http://localhost:4000/lab-website-demo` 로 접속하세요.

## 📝 콘텐츠 수정 방법

### 1. 연구실 정보 수정

각 섹션의 정보는 `_data/` 디렉토리의 YAML 파일에서 관리됩니다:

- **연구실 소개**: `_data/about.yml`
- **교수 정보**: `_data/professor.yml`
- **멤버 정보**: `_data/members.yml`
- **논문 목록**: `_data/publications.yml`
- **프로젝트**: `_data/projects.yml`
- **사진**: `_data/photos.yml`
- **채용 및 연락처**: `_data/recruit.yml`

### 2. 이미지 추가

이미지는 `assets/images/` 디렉토리에 추가하세요:

- **멤버 사진**: `assets/images/members/`
- **교수 사진**: `assets/images/professor/`
- **갤러리 사진**: `assets/images/photos/`
- **프로젝트 로고**: `assets/images/projects/`

### 3. 스타일 수정

스타일은 SCSS를 사용하여 모듈화되어 있습니다:

- **메인 스타일시트**: `assets/css/style.scss` - 모든 SCSS 모듈을 import하는 메인 파일
- **SCSS 모듈**: `_sass/` 디렉토리에 각 섹션별로 분리된 SCSS 파일들이 있습니다:
  - `_variables.scss`: 변수 정의
  - `_base.scss`: 기본 스타일
  - `_header.scss`, `_footer.scss`: 헤더/푸터 스타일
  - `_about.scss`, `_members.scss`, `_publications.scss` 등: 각 섹션별 스타일

특정 섹션의 스타일을 수정하려면 `_sass/` 디렉토리에서 해당 파일을 수정하세요.

## 🔧 GitHub Pages 배포

### 초기 배포 설정

1. **GitHub에 저장소 생성**
   
   저장소 이름: `lab-website-demo`

2. **코드 푸시**
   ```bash
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/kjeemin21/lab-website-demo.git
   git push -u origin main
   ```

3. **GitHub Pages 활성화**
   
   - GitHub 저장소 페이지로 이동
   - Settings → Pages 메뉴 선택
   - Source: "Deploy from a branch" 선택
   - Branch: `main` 브랜치의 `/root` 디렉토리 선택
   - Save 클릭

4. **배포 확인**
   
   몇 분 후 `https://kjeemin21.github.io/lab-website-demo`에서 사이트를 확인할 수 있습니다.

### 업데이트 배포

내용을 수정한 후 다음 명령어로 배포하세요:

```bash
git add .
git commit -m "Update content"
git push
```

GitHub가 자동으로 사이트를 다시 빌드하고 배포합니다.

## 📦 기술 스택

- **Jekyll**: 정적 사이트 생성기 (GitHub Pages gem을 통해 관리)
- **GitHub Pages**: 호스팅 플랫폼 및 Jekyll 의존성 관리
- **Minima**: Jekyll 테마
- **SCSS/Sass**: CSS 전처리기 (모듈화된 스타일 관리)
- **HTML5/CSS3**: 프론트엔드
- **YAML**: 데이터 형식

## 🐛 트러블슈팅

### 로컬에서 실행되지 않는 경우

1. Ruby 버전 확인:
   ```bash
   ruby --version
   ```
   Ruby 2.7.0 이상이어야 합니다.

2. Bundler 설치:
   ```bash
   gem install bundler
   ```

3. 의존성 재설치:
   ```bash
   bundle clean --force
   bundle install
   ```

### GitHub Pages 배포가 실패하는 경우

1. **GitHub Actions 탭 확인**
   
   저장소의 Actions 탭에서 빌드 로그를 확인하세요.

2. **_config.yml 확인**
   
   `baseurl`과 `url` 설정이 올바른지 확인하세요:
   ```yaml
   baseurl: "/lab-website-demo"
   url: "https://kjeemin21.github.io"
   ```

3. **Gemfile 확인**
   
   `gem "jekyll"`이 주석 처리되어 있고, `gem "github-pages"`가 활성화되어 있는지 확인하세요.

## 📄 라이선스

이 프로젝트는 연구 및 교육 목적으로 사용됩니다.

## 📧 문의

- **Email**: kjeemin21@gmail.com
- **GitHub**: [@kjeemin21](https://github.com/kjeemin21)

---

Built with ❤️ using Jekyll and GitHub Pages

