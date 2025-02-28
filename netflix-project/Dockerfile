# Use an official Ubuntu base image
FROM ubuntu:latest

# Set environment variable to avoid interactive prompts
ENV DEBIAN_FRONTEND=noninteractive

# Update package lists and install required packages
RUN apt update && apt install -y git apache2

# Clone the Netflix project repository into /var/www/html
RUN git clone https://github.com/CleverProgrammers/pwj-netflix-clone.git /tmp/netflix-clone

# Move project files to Apache's root directory
RUN mv /tmp/netflix-clone/* /var/www/html/

# Remove the now-empty cloned directory
RUN rm -rf /tmp/netflix-clone

# Set correct permissions for Apache
RUN chown -R www-data:www-data /var/www/html

# Expose port 80 to allow external traffic
EXPOSE 80

# Start Apache in the foreground
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]

