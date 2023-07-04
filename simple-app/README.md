# React Application

## Docker
Build image
```bash
docker build -t simple-app:latest .
```
Run container
```bash
docker run -d -p 80:80 --name conatiner-react simple-app:latest
```

## References

1. Basic react application w/ webpack: https://jsramblings.com/creating-a-react-app-with-webpack/  