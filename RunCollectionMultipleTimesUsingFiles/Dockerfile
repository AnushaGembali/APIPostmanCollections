FROM node:22.19.0

WORKDIR /app

RUN npm install -g newman newman-reporter-html newman-reporter-htmlextra

COPY RunTestsMultipleTimesUsingFilesCol.json .
COPY csvfile.csv .

CMD ["newman", "run", "RunTestsMultipleTimesUsingFilesCol.json", "-d", "csvfile.csv", "-r", "cli,html,htmlextra"]