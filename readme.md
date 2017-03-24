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
2) OoS для Multi-dimentional Scaling
  * На основе здравого смысла - Простой модификации алгоритма SMACOF применимой к 1 новой точке и работающей за O(nd), где n - количество точек в выборке обучения, а d - размерность пространства выборки.

Основная документация и инструкция по сборке http://scikit-learn.org/
