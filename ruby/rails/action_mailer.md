# Pass params hash to mailer
This can be useful if you don't want to change the params of a mailer, but still want to pass in some variables.
ie when you want to override a variable for testing purposes

`
ApplicationMailer.with(locale: :es).application_mail(user)
`

    ApplicationMailer < ActionMailer::Base
      # Might be able to pass a block to set_locale
      # and call I19n.with_locale(email, &block)
      # not 100% sure though
      before_action :set_locale
    
      def application_mail(email)
        I18n.with_locale(@locale) do 
          mail(to: email)
        end
      end
      private
    
      def set_locale
        @locale = params[:locale]
        @locale ||= get_locale(email)
      end
    end
