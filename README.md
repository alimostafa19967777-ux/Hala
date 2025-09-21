# bcbcvbcvn

    import pandas as pd

  
     FILE_ID = "1Ni4rvDTwdX5LpSsI8uur47ISeQ4fkRmW"  # ID файла на Google Drive


      file_url = f"https://drive.google.com/uc?id={FILE_ID}"

      raw_data = pd.read_csv(file_url)     # читаем файл

      raw_data.head(10) 
# ffb
