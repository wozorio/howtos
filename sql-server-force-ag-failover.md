# Force an Availability Group to go Online (AlwaysOn Cluster) on a particular node

Run the following command on SQL Management Studio:

`alter availability group <availability_group_name> force_failover_allow_data_loss`

After forcing an AG to go Online on a particular SQL AlwaysOn cluster node, the database syncrhonization is suspended, therefore, make sure you re-enable it again by running the SQL statement below on all SQL cluster nodes:

`ALTER DATABASE [YourDatabase] SET HADR RESUME`
