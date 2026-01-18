FROM python:3.13.11-slim
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/
WORKDIR /code
COPY pyproject.toml .python-version uv.lock ./

#Get the requirements passed to uv to update the python environment
RUN uv sync --locked 

#This allows skipping the "uv" "run" arguments
ENV PATH="/code/.venv/bin:$PATH"

COPY ingest_data.py .
#ENTRYPOINT ["uv", "run", "python", "pipeline.py"]
ENTRYPOINT ["python", "ingest_data.py"]