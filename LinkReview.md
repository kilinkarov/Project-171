| Title                                                                  | Year | Source                                                                                                           | Summary |
| :--------------------------------------------------------------------- | ---: | :--------------------------------------------------------------------------------------------------------------- | :---------- |
| GenImage: A Million-Scale Benchmark for Detecting AI-Generated Image                    | - | [paper](https://proceedings.neurips.cc/paper_files/paper/2023/file/f4d4a021f9051a6c18183b059117e8b5-Paper-Datasets_and_Benchmarks.pdf)| How to create AI-Generate dataset (GenImages)         |
| AI vs. AI: Can AI Detect AI-Generated Images?                     | 2023 | [paper](https://www.mdpi.com/2313-433X/9/10/199)| Method of detection GAN-images        |
| Zero-Shot Detection of AI-Generated Images                     | 2024 | [paper](https://arxiv.org/abs/2409.15875)| New method without AI-dataset     |
| Online Detection of AI-Generated ImagesOnline Detection of AI-Generated Images                     | 2023 | [paper](https://openaccess.thecvf.com/content/ICCV2023W/DFAD/html/Epstein_Online_Detection_of_AI-Generated_Images__ICCVW_2023_paper.html)|  Online-method for detection   |
| CIFAKE: Image Classification and Explainable Identification of AI-Generated Synthetic Images                   | 2024 | [paper](https://ieeexplore.ieee.org/abstract/document/10409290)|  Generated dataset   |
| Leveraging Frequency Analysis for Deep Fake Image Recognition                  | 2020 | [paper](http://proceedings.mlr.press/v119/frank20a)|  Frequency analysis for real and fake images|




0) Можно попробовать посмотреть на распределение цветов и в целом на цвета, которые используются в AI-гене, есть ощущение, что они одновременно более четкие и мыльные (как будто более мультяшные иногда) (очень странно, конечно, но попробуем позже это формализовать). Ешё на картинках часто размывается фон, не видел, чтобы это чекали. Ешё иногда объект выглядит как-будто вырезанным.
1) Судя по всему диффузионки побеждать сложнее всего. Существующие методы решения: ResNet-50, трансформаторы, Swin-T (кажется тоже трансформатор). Надо попробовать что-то не на основе нейронок. В решениях смотрят на расхождение частотных компонент(на AI и реальном) - F3NET. Этот метод похож на идею 0. Больинство детекторов предназнчены для GAN. Основная проблема: низкая обощающая способность. Мы можем использовать обученные на некотором генераторе только для него.Очень странно, что нет попыток результаты как-то совместить, мб поставить в классификации другой трэшхолд. Хотя, если честно, не понимаю, почему на валидации просто нельзя понять какая именно у нас нейронка, ну или хотя бы к какой мы идецно близки.
2) Снова про спектр - обнаружили, что в спектре Фурье действительно есть отличие: а именно пик интенсивности у сгенерированных изоюражений (именно у GAN!).Тут использовалисб 12 разных генеративок. Просто fine-tunning СNN
3) Попытка понять реальное распределение пикселей у реальных моделей. Идея в том, что реальные изображения соответсвуют своей стоимости кодирования, а нереальные нет (что это???)
4) А че бы не попробовать поюзать доделку реальных изображений некоторыми графическими редакторами. Мб что-то хорошее увидим. В статье основная идея вечного онлайн дообучения с появляпнием новых моделей. Там утверждают, что это работает и чем больше получаемм моделеф тем лучше будем работать в бущуем.
5) Создание датасета CIFAKE. Используется объяснимый ИИ (XAI)
