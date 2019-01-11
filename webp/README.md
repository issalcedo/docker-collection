# Run

docker run --rm -e "LD_LIBRARY_PATH=/usr/local/lib/" -a stdin -a stdout -v /Users/salci003/Workspace/docker/webp:/usr/local/webp webp cwebp foo.jpg -o bar.png