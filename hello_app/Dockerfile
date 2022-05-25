FROM python:3.7-slim-buster

WORKDIR /app

COPY . /app/


# hadolint ignore=DL3013
RUN pip install --upgrade pip && \
    pip install -trusted-host pypi.python.org -r requirements.txt

EXPOSE 80

CMD ["python","hello.py"]