# small-album

## Requirements
### version 0.1.0
- 클라우드 서비스(미정)에 저장된 이미지를 화면(브라우저?)에 번갈아가면서 보여준다.
- 구동환경은 라즈베리파이급으로 클라이언트 환경에서 접속하면 바로 실행된다. (사용자의 로그인 행동은 없음)
- 클라우드 서비스 접속정보, 화면 전환 등의 값은 설정파일(텍스트)로 관리한다.

## Preparation
- 서버 언어는 python, 프레임워크는 django를 사용한다.
- 클라이언트는 브라우저로 제한(v.0.1.0)로 제한한다.
- 클라우드서비스에 주기적으로 접속하여 파일을 다운로드받고 이를 보여준다.

## Features
- 사용자가 요청한 정보의 사진들을 클라이언트에 보여준다.
- 사용자가 요청한 정보의 사진들을 저장소에서 찾아낸다.
- 클라우드 서비스에 주기적으로 접속하여 파일을 다운로드 받아서 적절한 디렉토리에 저장한다.
- 설정 정보(클라우드 접속정보, 화면 전환 값, 클라우드 접속 주기)를 가져오고 요청에 따라 그 값을 알려준다.
- 설정 정보를 파일에서 읽어들인다.

## Developments
- Views
  - /albums: 기본 서비스 화면. 여러 개의 화면을 번갈아가면서 보여준다.
- Objects
  - Photos: 요청받은 사진을 찾아낸다. 요청 형태(sequential)에 따라 다음 사진 정보도 관리한다.
    - /photos: 첫 번째 사진을 반환한다. 다음 사진의 ID값도 반환한다.
    - /photos/123: ID 123인 사진을 반환한다. 다음 사진의 ID값도 반환한다. 
  - Batches: 주기적으로 클라우드 서비스에 접속하여 사진을 서버에 저장한다.
  - Configs: 설정 정보를 가져오고 조회한다(설정값 변경은 미포함).
  - ConfigFiles: 파일에서 설정 정보를 조회한다.

## Settings
- virtualenv --python=python3.6 venv
- source venv/bin/activate

- echo "venv/" >> .gitignore

- pip install django
- pip install djangorestframework

- pip freeze >> requirements.txt

- django-admin startproject smallalbum .

- python manage.py runserver
- ^C

