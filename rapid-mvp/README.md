# team-randomizer

Repository: https://github.com/VIN-DCSIL-Org/team-randomizer

## Pre-requisites

- `uv`
- `node` v22+

## Local Setup

1. In the `my-react-app` folder, run:

	```bash
	npm install
	npm run dev
	```

2. In another terminal, in the `backend` folder, run:

	```bash
	uv sync
	uv run fastapi dev app/main.py
	```

3. Open the app in your browser:

	http://localhost:5173/
