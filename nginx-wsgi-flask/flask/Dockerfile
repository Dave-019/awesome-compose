FROM python:3.9.2-alpine
RUN apk add curl
RUN adduser -D nonroot
RUN mkdir /home/app/ && chown -R nonroot:nonroot /home/app
RUN mkdir -p /var/log/flask-app && touch /var/log/flask-app/flask-app.err.log && touch /var/log/flask-app/flask-app.out.log
RUN chown -R nonroot:nonroot /var/log/flask-app
WORKDIR /home/app
COPY --chown=nonroot:nonroot . .
RUN python -m venv /home/app/venv
ENV PATH="/home/app/venv/bin:$PATH"
RUN pip install --upgrade pip
RUN pip install -r requirements.txt
EXPOSE 8000
CMD ["gunicorn", "-w", "3", "-t", "60", "-b", "0.0.0.0:8000", "app:app"]
