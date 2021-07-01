https://www.mikeperham.com/2021/04/20/a-tour-of-the-sidekiq-api/o

#how to delete retry set:
`
rs.scan("AJob").select { |j| j.display_class == "AJob" }.map(&:delete)
rs.scan("AJob").count { |j| j.display_class == "AJob" }
`
