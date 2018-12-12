# terraform-aws-cloudwatch-ec2-recovery


example:
```hcl

resource "aws_instance" "web" {
  ami           = "${data.aws_ami.rhel.id}"
  instance_type = "t2.micro"
  tags {
    Name = "TestInstance"
  }
}



module "test_module" {
  source = "github.com/EidosMedia/terraform-aws-cloudwatch-ec2-recovery.git"
  count = 1
  ec2_instances   = { names = ["TestInstance"] , ids = ["${aws_instance.web.id}"] }
  sns_mail_topic = "arn:aws:sns:XXXXXXXXXX"
}

```
