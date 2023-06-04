
- [1 GCP -\> AWS](#1-gcp---aws)
  - [\[AWS SAA-C03\]](#aws-saa-c03)
  - [Luyện thi](#luyện-thi)
  - [Đi thi](#đi-thi)






# 1 member of AWS Study Group




[AWS SAA-C03]

Chia sẻ một chút về trải nghiệm thi của mình. Mình chỉ có kinh nghiệm GCP mới tìm hiểu sang AWS, chỉ biết cơ bản 1 số dịch vụ cơ bản như S3, Lambda trước đó. Mình định thi cuối tháng 7 nhưng do cái free retake voucher hết hạn ngày 31/5 nên mình thi trước lần 1 để luyện tập nhưng mà kết quả pass luôn.

Luyện thi:

- Khóa học của Stephane Maarek ở Udemy
- Mình thi trước khi luyện đề nên chưa kịp làm gì cả chỉ note lại kiến thức đã học trên udemy.

Đi thi:

- Mình thi tại Thaison ICT Training Center, có request thêm 30p. Do mình chưa chuẩn bị kĩ nên làm hết thời gian, chỉ có thừa thời gian để review lại những câu flagged
- Về một số câu hỏi trong đề thi:
- Files > 200GB, yêu cầu remove PII files and automation remediations. (Câu này mình định chọn Amazon Macie mà thấy yêu cầu automation remediation nên mình chọn phương án không dùng Macie nhưng có automation remove files)
- AWS System manager vs CloudFormation
- Aws secret manager vs aws parameter store
- AWS ACM
- Egress-only Internet Gateway cho IPv6
- AWS batch vs Lambda
- S3 Glacier Storage Expedited vs Standard (Yêu cầu restore trong 5p)
- Chọn IAM role vs IAM policy
- Chọn loại EC2 Instances Purchasing Options. Câu này chắc chắn phải học hết các loại.
- AWS storage gateway
- SMB clients use Amazon FSx File Gateway
- AWS Organization
- AWS Directory Services vs IAM Identity Center
- Node cant connect to the EKS control plane
- VPC endpoints
- 1 câu về việc dùng quá tiền billing giữa các accounts trong Organization nhưng câu này mình không hiểu lắm nên khoanh random.
- 3 4 câu về SNS SQS nhưng khá cơ bản: FIFO, DLQ, Fanout
- Đang dùng cho 2 dịch vụ lamdba và EC2, yêu cầu chọn Compute Savings Plans hay EC2 Instance Savings Plans
- Amazon CloudFront distribution for reduce latency for the static data and dynamic data .
- Give access Amazon CloudWatch dashboard cho product manager không có AWS account. Câu này yêu cầu least privilege nên mình chọn share qua CloudWatch console dùng PM email.
- 1 câu AWS EFS + ASG Multi AZ, yêu cầu chọn storage khi files output của app size from tens of gigabytes to hundreds of terabytes, stored dạng standard file system structure.
- Setting inbound Security Group gắn vào database để chỉ có EC2 ở private subnet can access to databases ở dedicated subnet.
- Authen dùng Cognito User Pools
- Fix lỗi network khi NACL và Security Group đang để default.
- Migrate analytics application using EC2 and Mysql database scale seemlessly -> Chọn ASG AMI template dùng spot fleet và Amazon Aurora MySQL

Tổng quan thì mình thấy hầu như các đáp án sẽ thiên hướng chọn dịch vụ của aws, serverless. Cần chú ý 1 số limit của các dịch vụ để chọn khi gặp một số câu có thông số, và quan trọng nhất là đọc yêu cầu viết chữ in hoa ở câu hỏi như LEAST operational, cost-effective,....

Chúc các bạn chuẩn bị tốt!