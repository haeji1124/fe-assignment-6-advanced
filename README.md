## 개요

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/83c75a39-3aba-4ba4-a792-7aefe4b07895/6912169d-ce70-41bf-b624-946d4ee984eb/Untitled.png)

GitHub Actions에 워크플로우를 작성해 다음과 같이 배포가 진행되도록 함

1. 저장소를 체크아웃합니다.
2. Node.js 18.x 버전을 설정합니다.
3. 프로젝트 의존성을 설치합니다.
4. Next.js 프로젝트를 빌드합니다.
5. AWS 자격 증명을 구성합니다.
6. 빌드된 파일을 S3 버킷에 동기화합니다.
7. CloudFront 캐시를 무효화합니다.

## 주요 링크

- S3 버킷 웹사이트 엔드포인트: _________
- CloudFrount 배포 도메인 이름: _________

## 주요 개념

- GitHub Actions과 CI/CD 도구: _________
- S3와 스토리지: _________
- CloudFront와 CDN: _________
- 캐시 무효화(Cache Invalidation): _________
- Repository secret과 환경변수: _________
