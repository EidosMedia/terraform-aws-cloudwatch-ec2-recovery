# terraform-aws-cloudwatch-ec2-recovery


example:

resource "aws_instance" "web" {
  ami           = "${data.aws_ami.rhel.id}"
  instance_type = "t2.micro"
  tags {
    Name = "TestInstance"
  }
}



module "test_module" {
  source = "github.com/rafstef/terraform-aws-cloudwatch-ec2-recovery.git"
  count = 1
  ec2_instances   = { names = ["TestInstance"] , ids = ["${aws_instance.web.id}"] }
}