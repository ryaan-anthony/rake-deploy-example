require 'power-rake'

INIT_BACKEND = [
  "--backend-config bucket=#{PowerRake.config.backend['bucket']}",
  "--backend-config dynamodb_table=#{PowerRake.config.backend['lock_table']}",
  "--backend-config key=#{PowerRake.config.project}/#{PowerRake.current_env}.tfstate"
].join(' ')

TF_SOURCE_PATH = PowerRake.config.source_path

TF_VARS = [
  "--var certificate_arn=#{PowerRake.config.certificate_arn}",
  "--var environment=#{PowerRake.current_env}",
  "--var instance_ami=#{PowerRake.config.instance['ami']}",
  "--var instance_count=#{PowerRake.config.instance['count']}",
  "--var instance_type=#{PowerRake.config.instance['type']}",
  "--var instance_user=#{PowerRake.config.instance['user']}",
  "--var project=#{PowerRake.config.project}",
  "--var vpc_id=#{PowerRake.config.vpc_id}"
].join(' ')

task :init do
  try? "terraform init #{INIT_BACKEND} #{TF_SOURCE_PATH}"
end

task :plan do
  try? "terraform plan #{TF_VARS} #{TF_SOURCE_PATH}"
end

task :apply do
  try? "terraform apply #{TF_VARS} #{TF_SOURCE_PATH}"
end

task :destroy do
  try? "terraform destroy #{TF_VARS} #{TF_SOURCE_PATH}"
end
