Cyclistic Project

Business Problem Understanding
------------
Problem Statement
------------
Karena harga rumah yang sangat bervariasi, maka menentukan harga rumah yang sesuai sangatlah penting bagi yang ingin menjual dan membeli rumah.

Salah satu tantangan terbesar bagi agen properti/broker adalah pemecahan masalah untuk dapat memiliki model bisnis yang menguntungkan secara finansial, serta dapat memberikan pengalaman positif penjual dan pembeli rumah.

Mengingat kebebasan penuh kepada pemilik rumah untuk menentukan harga rumah mereka, dengan hanya memberikan petunjuk minimal yang memungkinkan tuan rumah membandingkan tempat serupa di lingkungan mereka untuk mendapatkan harga yang kompetitif. Pemilik rumah pun dapat memasukkan harga yang lebih tinggi untuk fasilitas tambahan apa pun yang mereka anggap perlu. Dengan meningkatnya jumlah jual beli rumah, menentukan harga yang tepat untuk dapat kompetitif di lingkungan sekitar sangatlah penting.

Goals
------------
Berdasarkan permasalahan tersebut, kita sebagai agen properti/broker tentu perlu menggunakan 'tool' yang dapat memprediksi serta membantu (dalam hal ini jual beli rumah) untuk dapat menentukan harga rumah yang tepat. Adanya perbedaan pada berbagai fitur yang terdapat pada suatu rumah, lokasi, umur rumah, jumlah ruangan, jumalah kamar tidur, rumah tangga, dan jarak dengan pantai akan menambah keakuratan prediksi harga rumah, yang mana dapat mendatangkan keuntungan bagi agen properti/broker.

Bagi pembeli rumah, prediction tool yang dapat memberikan prediksi harga secara fair tentu dapat meningkatkan nilai investasi rumah yang dibeli.

Analytic Approach
------------
Jadi, yang perlu kita lakukan adalah menganalisis data untuk dapat menemukan pola dari fitur-fitur yang ada, yang membedakan harga satu rumah dengan yang lainnya. 

Selanjutnya, kita akan membangun suatu model regresi yang akan membantu agen properti/broker untuk dapat menyediakan 'tool' prediksi harga rumah yang baru masuk dalam daftar, yang mana akan berguna untuk agen properti/broker dalam menentukan harga listing-nya.

Metric Evaluation
------------
Evaluasi metrik yang akan digunakan adalah RMSE, MAE, dan MAPE, di mana RMSE adalah nilai rataan akar kuadrat dari error, MAE adalah rataan nilai absolut dari error, sedangkan MAPE adalah rataan persentase error yang dihasilkan oleh model regresi. Semakin kecil nilai RMSE, MAE, dan MAPE yang dihasilkan, berarti model semakin akurat dalam memprediksi harga sewa sesuai dengan limitasi fitur yang digunakan. 

Selain itu, kita juga bisa menggunakan nilai R-squared atau adj. R-squared jika model yang nanti terpilih sebagai final model adalah model linear. Nilai R-squared digunakan untuk mengetahui seberapa baik model dapat merepresentasikan varians keseluruhan data. Semakin mendekati 1, maka semakin fit pula modelnya terhadap data observasi. Namun, metrik ini tidak valid untuk model non-linear.

Conclusion
------------
Berdasarkan pemodelan yang sudah dilakukan, fitur 'ocean_proximity' dan 'rooms_per_household' menjadi fitur yang paling berpengaruh terhadap 'median_house_value'.

 Metrik evaluasi yang digunakan pada model adalah nilai RMSE, MAE & MAPE. Jika ditinjau dari nilai MAPE yang dihasilkan oleh model setelah dilakukan hyperparameter tuning, yaitu sebesar 15%, kita dapat menyimpulkan bahwa bila nanti model yang kita buat ini digunakan untuk memperkirakan harga rumah di California pada rentang nilai seperti yang dilatih terhadap model (maksimal harga USD 452500), maka perkiraan harganya rata-rata akan meleset kurang lebih sebesar 15% dari harga seharusnya. 
 
 Tetapi, tidak menutup kemungkinan juga prediksinya meleset lebih jauh karena bias yang dihasilkan model masih cukup tinggi bila dilihat dari visualisasi antara harga aktual dan prediksi. Bias yang dihasilkan oleh model ini dikarenakan oleh terbatasnya fitur pada dataset.

 Model ini tentu masih dapat diimporvisasi agar dapat menghasilkan prediksi yang lebih baik lagi. Namun, kita dapat melakukan A/B testing terhadap model yang sudah dibuat pada project ini untuk mengetahui tingkat efektifitas penggunaan model terhadap peningkatan keuntungan agen properti/broker. Nantinya, dari hasil A/B testing, kita bisa mendapatkan insight lainnya terkait perihal yang bisa dan harus diperbaiki pada model.

Recommendations
------------
Lakukan A/B testing untuk menguji tingkat efektivitas model terhadap keuntungan yang didapat agen properti/broker.

Lalu, hal-hal yang dapat dilakukan untuk mengembangkan model agar lebih baik lagi, seperti:

1. Mengecek prediksi mana saja yang memiliki nilai error yang tinggi. Kita dapat mengelompokkan error tersebut ke dalam grup overestimation dan underestimation, lalu memilih 5% error paling ekstrim saja untuk tiap grup. Nantinya pengelompokkan akan menjadi 3 grup, yaitu overestimation (5%), underestimation (5%), dan grup mayoritas yang error-nya mendekati nilai mean (90%). Setelahnya kita bisa mengecek hubungan antara error tersebut dengan tiap variabel independen. Pada akhirnya kita dapat mengetahui sebenarnya variabel mana saja dan aspek apa yang menyebabkan model menghasilkan error yang tinggi, sehingga kita bisa melakukan training ulang dengan penerapan feature engineering lainnya.
<br><br>   
1. Jika memungkinkan, penambahan fitur yang lebih korelatif dengan target ('median_house_value'), seperti luas tanah dan luas bangunan. Selain itu, adanya penambahan data terkini untuk harga rumah tentu akan dapat mengimprovisasi kapasitas prediksi dari model.
<br><br>   
3. Jika ada penambahan banyak data, dapat dicoba dengan menggunakan model yang lebih kompleks, seperti recursive neural networks (RNN). Namun, kalau jumlah data dan fiturnya masih seperti dataset ini, kemungkinan besar tidak akan mengubah hasilnya secara signifikan.
<br><br>   
4. Model yang sudah dibangun ini bisa dimanfaatkan untuk pengembangan pembuatan model lainnya. Contohnya seperti pembuatan model untuk memprediksi update harga rumah.


==============================

Design marketing strategies aimed at converting casual riders into annual members.

Project Organization
------------

    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third-party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- Documentation of your project
    │
    ├── notebooks          <- Jupyter notebooks. The naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results-oriented visualizations
    │       └── visualize.py
    │
    └── references         <- Data dictionaries, manuals, and all other explanatory materials.


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
