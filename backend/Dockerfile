FROM python:3.12.11-slim-bookworm
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1
WORKDIR /app
RUN groupadd --system app && useradd --system --gid app --home-dir /app app
COPY requirements.txt .
# RUN pip install --no-cache-dir --upgrade pip && \
#     pip install --no-cache-dir -r requirements.txt
RUN pip install --no-cache-dir --retries 10 --timeout 120 -r requirements.txt
COPY --chown=app:app app.py .
ARG APP_VERSION=dev
ENV APP_VERSION=$APP_VERSION
USER app
EXPOSE 5000
CMD ["python", "app.py"]
