pipeline
{
    agent any

    stages
    {
        stage('create vpc')
        {
            steps
            {
		        sh 'AWS_REGION="ap-south-1"
                            VPC_NAME="My VPC"
                            VPC_CIDR="10.0.0.0/16"
                            SUBNET_PUBLIC_CIDR="10.0.1.0/24"
                            SUBNET_PUBLIC_AZ="ap-south-1a"
                            SUBNET_PUBLIC_NAME="10.0.1.0 - ap-south-1a"
                            SUBNET_PRIVATE_CIDR="10.0.2.0/24"
                            SUBNET_PRIVATE_AZ="ap-south-1c"
                            SUBNET_PRIVATE_NAME="10.0.2.0 - ap-south-1b"
                            CHECK_FREQUENCY=5

                            echo "Creating VPC in preferred region..."
                            VPC_ID=$(aws ec2 create-vpc \
                              --cidr-block $VPC_CIDR \
                              --query 'Vpc.{VpcId:VpcId}' \
                              --output text \
                              --region $AWS_REGION)
                            echo "  VPC ID '$VPC_ID' CREATED in '$AWS_REGION' region."
                            # Add Name tag to VPC
                            aws ec2 create-tags \
                              --resources $VPC_ID \
                              --tags "Key=Name,Value=$VPC_NAME" \
                              --region $AWS_REGION 
                            echo "  VPC ID '$VPC_ID' NAMED as '$VPC_NAME'."'
            }
        }
    }
}
