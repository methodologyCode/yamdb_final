FROM python:3.7-slim

# Enter or create.
WORKDIR /app

# api_yamdb/ -> /app
COPY . .

RUN pip3 install -r /app/requirements.txt --no-cache-dir 

# Run the server during the start of the container.
CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]
