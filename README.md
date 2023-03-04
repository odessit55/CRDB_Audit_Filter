To filter CRDB audit log:
//   relying on a string
// User":"‹userName›","DescriptorID
// being unique
// example of filtering out a single one
tail -f  cockroach-sql-audit.log | stdbuf -o0 grep -v 'User":"‹application›","DescriptorID' >>audit.log
// we can create a script that would pull user names to be filtered out from file/table and build
// appropriate script to run continuously
// example: filter out both application and alex   
tail -f  cockroach-sql-audit.log | stdbuf -o0 grep -v 'User":"‹application›","DescriptorID' |  stdbuf -o0 grep -v 'User":"‹alex›","DescriptorID' >>audit.log
