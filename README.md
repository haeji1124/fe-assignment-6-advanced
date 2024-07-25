## 배포 Flow
GitHub Actions에 워크플로우를 작성해 다음과 같이 배포가 진행되도록 함
  1. 저장소를 체크아웃합니다.
  2. Node.js 18.x 버전을 설정합니다.
  3. 프로젝트 의존성을 설치합니다.
  4. Next.js 프로젝트를 빌드합니다.
  5. AWS 자격 증명을 구성합니다.
  6. 빌드된 파일을 S3 버킷에 동기화합니다.
  7. CloudFront 캐시를 무효화합니다.

배포를 위해 Repository secret과 환경변수를 설정합니다.
- AWS_ACCESS_KEY_ID : IAM user의 액세스 키
- AWS_SECRET_ACCESS_KEY: IAM user의 비밀 맥세스 키
- AWS_REGION : s3 버킷의 region
- CLOUDFRONT_DISTRIGUTION_ID: ClounFront distribution ID

![image](https://github.com/user-attachments/assets/5ea0f688-90aa-4854-8748-e955e6decbdd)


사용자가 웹사이트 접속했을 때 CloudFront에 캐시가 있다면 정적파일 반환되고 없다면 S3에 정적파일을 요청해서 CloudFront가 정적파일을 가지고 있게 된다.
깃 repo에서 commit이 발생하면 CI 파이프라인에 의해 빌드가 되고 산출물이 S3에 업로드 된다.

## 주요 링크

- S3 버킷 웹사이트 엔드포인트: http://hanghae-front.s3-website.ap-northeast-2.amazonaws.com/
- CloudFrount 배포 도메인 이름: [https://d2djy75mjwwhun.cloudfront.net/](https://d2r48sh5zmucq8.cloudfront.net/)

## 주요 개념

- GitHub Actions과 CI/CD 도구: GitHub에서 제공하는 자동화된 워크플로우 실행 도구로, 코드 변경 시 자동으로 빌드, 테스트, 배포 등의 작업을 수행할 수 있게 해준다.
- S3와 스토리지: Amazon Simple Storage Service의 약자로, 확장성이 뛰어난 객체 스토리지 서비스이다. 웹 호스팅에도 사용될 수 있어 정적 웹사이트를 호스팅하는 데 적합하다.
- CloudFront와 CDN: Amazon의 콘텐츠 전송 네트워크(CDN) 서비스로, 전 세계에 분산된 엣지 로케이션을 통해 콘텐츠를 빠르게 전달한다. S3와 함께 사용하여 웹사이트의 성능을 향상시킬 수 있다.
- 캐시 무효화(Cache Invalidation): CDN의 엣지 로케이션에 저장된 캐시된 콘텐츠를 강제로 새로고침하는 프로세스이다. 이를 통해 업데이트된 콘텐츠를 즉시 사용자에게 제공할 수 있다.
- Repository secret과 환경변수: GitHub 리포지토리에 안전하게 저장되는 암호화된 환경 변수다. AWS 접근 키와 같은 민감한 정보를 저장하는 데 사용되며, 워크플로우 실행 중에 안전하게 접근할 수 있다.
