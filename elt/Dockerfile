FROM python:3.8-slim

# Install PostgreSQL command-line tools
RUN apt-get update && apt-get install -y postgresql-client-15 cron

COPY start.sh /app/start.sh

# Copy the ELT script 
COPY elt_script.py .

WORKDIR /app

RUN echo "0 3 * * * python /app/elt_script.py" | crontab-

# Set the default command to run the ELT script
CMD ["python", "elt_script.py"]