# Small annotated dataset 
- To change the dataset directory in jupyter
```
cat /root/.config/Ultralytics/settings.json 
!sed -i 's/"datasets_dir": "\/content\/",/"datasets_dir": "\/",/' /root/.config/Ultralytics/settings.json
```
