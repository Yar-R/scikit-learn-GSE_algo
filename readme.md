Проектная работа студента 152 группы ФКН НИУ ВШЭ - Ребенко Ярослава Алексеевича.

Цели

0) изучение библиотеки scikit-learn
1) реализация алгоритмов Out of Sample для Multi-dimensional Scaling и для Spectral Embedding
2) групповая реализация алгоритма Грассмана-Штифеля
3) Реализация алгоритмов восстановления для упомянутых способов уменьшения размерности

Положение на момент 24 марта 2017:

Реализованы:

1) OoS для Spectral Embedding
  * На основе статьи "Out-of-Sample Extensions for LLE, Isomap, MDS, Eigenmaps, and Spectral Clustering" Yoshua Bengio, Jean-François Paiement and Pascal Vincent.
  * С учётом использования в scikit-learn нормированной версии Лапласиана.
  * на данный момент работает только для affinity="nearest_neighbors", eigen_solver='arpack'
2) reconstruct (inverse) для SE
  * на основе среднего n ближайших
3) OoS для Multi-dimentional Scaling
  * На основе модификации алгоритма SMACOF применимой к 1 новой точке и работающей за O(nd), где n - количество точек в выборке обучения, а d - размерность пространства выборки.
  * на данный момент работает только для metric=True, dissimilarity="eucledian"

n_neighbors = 10<br>
n_components = 2<br>
se = SpectralEmbedding(n_components=n_components, n_neighbors=n_neighbors, out_of_sample=True)<br>
dataset_embedding = se.fit_transform(dataset)<br>
new_points_embedding = np.array(list(<br>
    se.transform(point.reshape(1, -1))<br>
    for point in new_points<br>
))<br>
mds = MDS(n_components=n_components)<br>
dataset_embedding = mds.fit_transform(dataset)<br>
new_points_embedding = np.array(list(<br>
    mds.transform(point.reshape(1, -1), dataset)<br>
    for point in new_points<br>
))<br>
где dataset и new_points точки на вкладываемом многообразии


Зависимости:

1) Python (>= 2.6 or >= 3.3),
2) NumPy (>= 1.6.1),
3) SciPy (>= 0.9).
  
Сборка:

1) Необходимые для сборки пакеты
  - sudo apt-get install build-essential python3-dev python3-setuptools python3-numpy python3-scipy libatlas-dev libatlas3gf-base
2) В директории с исходниками:
  - pip install
3) Тестирование:
  - python setup.py build_ext --inplace
  - nosetests -v sklearn/
