---
title: Развертывание моделей (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], about deployment packages
- deployment packages [Master Data Services]
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 58f946f89691a6e26ba4402166b8ad725e7a977c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52761786"
---
# <a name="deploying-models-master-data-services"></a>Развертывание моделей (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]пакет представляет собой XML-файл, содержащий развертываемую структуру модели и (необязательно) данные этой модели. Пакеты модели используется для перемещения копий моделей из одной среды служб MDS в другую, либо для создания новых моделей в существующей среде MDS.  
  
> [!IMPORTANT]  
>  Пакеты могут быть развернуты только в выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , в котором они были созданы. Это означает, что пакеты, созданные в среде [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] , не могут быть развернуты в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] или более поздних версиях.  
  
## <a name="tools-for-deploying-models"></a>Инструменты для развертывания моделей  
 Для работы с пакетами модели можно использовать одно из трех средств, в зависимости от задач, которые требуется выполнить.  
  
-   **Средство MDSModelDeploy**: Средство MDSModelDeploy.exe используется для создания и развертывания объектов и данных модели. Если вы выбрали путь по умолчанию при установке служб MDS, это средство находится в папке *диск*: \Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.  
  
-   **Мастер развертывания модели**: Чтобы создать и развернуть только пакеты структуры модели, воспользуйтесь мастером веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Этот мастер нельзя использовать для развертывания данных.  
  
-   **Редактор пакета модели**: Для изменения пакета модели используйте программу ModelPackageEditor.exe, которая запускает мастер изменения пакета модели. С помощью этого мастера выполняется изменения пакета, созданного средством MDSModelDeploy или мастером развертывания модели. Если вы выбрали путь по умолчанию при установке служб MDS, это средство находится в папке *диск*: \Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.  
  
> [!IMPORTANT]  
>  MDSDeployModel можно использовать для создания новой модели или клона модели или обновления существующей модели и ее данных. Если средство MDSModelDeploy используется для обновления существующей модели и ее данных и пакет не содержит сущность, атрибут или элемент, имеющиеся в целевой модели, MDSModelDeploy не удаляет из модели эту сущность, атрибут или элемент.  
  
## <a name="what-packages-contain"></a>Содержимое пакетов  
 Пакет модели представляет собой XML-файл, сохраняемый с расширением PKG. При создании развертываемого пакета в него по желанию можно включить данные. Если данные решено включить, то нужно выбрать для них версию.  
  
 В пакет включаются все объекты модели. Эти объекты включают в себя:  
  
-   Сущности  
  
-   Атрибуты  
  
-   Группы атрибутов  
  
-   Иерархии  
  
-   Коллекции  
  
-   Бизнес-правила  
  
-   Флаги версии  
  
-   Представления подписки  
  
 Пользовательские метаданные, атрибуты файлов и разрешения пользователей и групп не включаются. При развертывании модели их нужно обновить вручную.  
  
## <a name="sample-packages"></a>Образцы пакетов  
 При установке служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]также копируются файлы образцов пакетов. Эти файлы пакетов расположены в каталоге Master Data Services\Samples\Packages, где установлена среда [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. При развертывании этих образцов пакетов с помощью средства MDSModelDeploy создаются и заполняются данными образцы моделей.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Средство MDSModelDeploy используется для создания новых пакетов объектов модели и данных.|[Создание пакета развертывания модели при помощи MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Создать новый пакет развертывания объектов модели можно только с помощью мастера.|[Создание пакета развертывания модели с помощью мастера](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|Средство MDSModelDeploy используется для развертывания пакета объектов модели и данных.|[Развертывание пакета развертывания модели при помощи MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Развернуть пакет объектов модели можно только с помощью мастера.|[Развертывание пакета развертывания модели с помощью мастера](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|Изменять пакет развертывания модели необходимо в тех случаях, когда требуется развернуть только определенные части модели, а не всю модель.|[Изменение пакета развертывания модели](../../2014/master-data-services/edit-a-model-deployment-package.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Варианты развертывания модели (службы Master Data Services)](model-deployment-options-master-data-services.md)  
  
  
