https://www.mikeperham.com/2021/04/20/a-tour-of-the-sidekiq-api/o

# Delete retry set:

`
rs.scan("AJob").select { |j| j.display_class == "AJob" }.map(&:delete)
`

# Count Retry set:

`
rs.scan("AJob").count { |j| j.display_class == "AJob" }
`
