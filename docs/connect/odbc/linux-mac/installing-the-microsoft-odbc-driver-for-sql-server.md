---
title: Установка Microsoft ODBC Driver for SQL Server на Linux и macOS | Документы Майкрософт
ms.custom: ''
ms.date: 12/04/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver, installing
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: MightyPen
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: a9e02676c12cf3257ba509dbee46cf46f5e0f876
ms.sourcegitcommit: 2ab79765e51913f1df6410f0cd56bf2a13221f37
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/27/2019
ms.locfileid: "56956045"
---
# <a name="installing-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Установка Microsoft ODBC Driver for SQL Server на Linux и macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этой статье описывается установка [!INCLUDE[msCoName](../../../includes/msconame_md.md)] драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на Linux и macOS, а также дополнительные средства командной строки для SQL Server (`bcp` и `sqlcmd`) и разработки заголовков unixODBC.

## <a name="microsoft-odbc-driver-17-for-sql-server"></a>Microsoft ODBC Driver for SQL Server версии 17 

> [!IMPORTANT]
> Если вы установили версии 17 `msodbcsql` пакет, который был кратко доступен, его следует удалить перед установкой `msodbcsql17` пакета. Это позволит избежать конфликта. `msodbcsql17` Пакет можно установить параллельно с `msodbcsql` v13 пакета.

### <a name="debian-8-and-9"></a>Debian 8 и 9
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#Debian 8
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Debian 9
curl https://packages.microsoft.com/config/debian/9/prod.list > /etc/apt/sources.list.d/mssql-release.list

exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="redhat-enterprise-server-6-and-7"></a>RedHat Enterprise Server 6 и 7
```
sudo su

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#RedHat Enterprise Server 6
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo

#RedHat Enterprise Server 7
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo

exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="suse-linux-enterprise-server-11sp4-12-and-15"></a>SUSE Linux Enterprise Server 11SP4, 12 и 15

```
sudo su

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#SUSE Linux Enterprise Server 11 SP4
zypper ar https://packages.microsoft.com/config/sles/11/prod.repo

#SUSE Linux Enterprise Server 12
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo

#SUSE Linux Enterprise Server 15
zypper ar https://packages.microsoft.com/config/sles/15/prod.repo
SUSEConnect -p sle-module-legacy/15/x86_64

exit
sudo ACCEPT_EULA=Y zypper install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="ubuntu-1404-1604-1710-and-1804"></a>Ubuntu 14.04, 16.04, 17.10 и 18.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#Ubuntu 14.04
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 16.04
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 18.04
curl https://packages.microsoft.com/config/ubuntu/18.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 18.10
curl https://packages.microsoft.com/config/ubuntu/18.10/prod.list > /etc/apt/sources.list.d/mssql-release.list

exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```
> [!NOTE]
> - Драйвер версии 17.2 или более поздней версии необходим для поддержки Ubuntu 18.04.
> - Версия драйвера 17.3 или более поздней версии необходим для поддержки Ubuntu 18.10.   

### <a name="os-x-1011-el-capitan-macos-1012-sierra-macos-1013-high-sierra-and-macos-1014-mojave"></a>OS X 10.11 (El Capitan), macOS 10.12 (Sierra), macOS 10.13 (High Sierra) и macOS 10.14 (Mojave)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql17 mssql-tools
```

## <a name="microsoft-odbc-driver-131-for-sql-server"></a>Microsoft ODBC Driver for SQL Server версии 13.1 

### <a name="debian-8"></a>Debian 8
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="redhat-enterprise-server-6"></a>RedHat Enterprise Server 6
```
sudo su
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="redhat-enterprise-server-7"></a>RedHat Enterprise Server 7
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="suse-linux-enterprise-server-11"></a>SUSE Linux Enterprise Server 11

```
sudo su
zypper ar https://packages.microsoft.com/config/sles/11/prod.repo
exit
sudo ACCEPT_EULA=Y zypper install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12

```
sudo su
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo
exit
sudo ACCEPT_EULA=Y zypper install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="ubuntu-1510"></a>Ubuntu 15.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="ubuntu-1604"></a>Ubuntu 16.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="ubuntu-1610"></a>Ubuntu 16.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="os-x-1011-el-capitan-and-macos-1012-sierra"></a>OS X 10.11 (El Capitan) и macOS 10.12 (Sierra)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql@13.1.9.2 mssql-tools@14.0.6.0
```

## <a name="microsoft-odbc-driver-13-for-sql-server"></a>Microsoft ODBC Driver for SQL Server версии 13

### <a name="redhat-enterprise-server-6"></a>RedHat Enterprise Server 6
```
sudo su
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo yum install unixODBC-utf16-devel #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="redhat-enterprise-server-7"></a>RedHat Enterprise Server 7
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo yum install unixODBC-utf16-devel #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="ubuntu-1510"></a>Ubuntu 15.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql=13.0.1.0-1 mssql-tools=14.0.2.0-1
sudo apt-get install unixodbc-dev-utf16 #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="ubuntu-1604"></a>Ubuntu 16.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql=13.0.1.0-1 mssql-tools=14.0.2.0-1
sudo apt-get install unixodbc-dev-utf16 #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12

```
sudo su 
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo 
zypper update 
sudo ACCEPT_EULA=Y zypper install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
zypper install unixODBC-utf16-devel
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="offline-installation"></a>Автономная установка
Если вы предпочитаете, требуют [!INCLUDE[msCoName](../../../includes/msconame_md.md)] драйвер ODBC 13 для установки на компьютере с подключением к Интернету, необходимо будет вручную устранить зависимости пакетов. [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 имеет прямой зависимости, приведенные ниже:
- Ubuntu: libc6 (> = 2.21), libstdc ++ 6 (> = 4.9), libkrb5-3 "," libcurl3 "," openssl "," debconf (> = 0,5), unixodbc (> = 2.3.1-1)
- Red Hat: ```glibc, e2fsprogs, krb5-libs, openssl, unixODBC```
- SuSE: ```glibc, libuuid1, krb5, openssl, unixODBC```

Каждый из этих пакетов в свою очередь имеет свои собственные зависимости, которые могут или не присутствовать в системе. Общее решение этой проблемы, см. в документации по вашему дистрибутиву пакета диспетчера: [Redhat](https://wiki.centos.org/HowTos/CreateLocalRepos), [Ubuntu](https://unix.stackexchange.com/questions/87130/how-to-quickly-create-a-local-apt-repository-for-random-packages-using-a-debian), и [SUSE](https://en.opensuse.org/Portal:Zypper)

Также часто бывает вручную загрузить все зависимые пакеты и помещать их на компьютере, а затем вручную установить каждый пакет, в свою очередь, окончания работы [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 пакета.

#### <a name="redhat-linux-enterprise-server-7"></a>Redhat Linux Enterprise Server 7
  - Загрузите последнюю версию `msodbcsql` `.rpm` отсюда: https://packages.microsoft.com/rhel/7/prod/
  - Установка зависимостей и драйвер
  
```
yum install glibc e2fsprogs krb5-libs openssl unixODBC unixODBC-devel #install dependencies
sudo rpm -i  msodbcsql-13.1.X.X-X.x86_64.rpm #install the Driver
```

#### <a name="ubuntu-1604"></a>Ubuntu 16.04
- Загрузите последнюю версию `msodbcsql` `.deb` отсюда: https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/ 
- Установка зависимостей и драйвер 

```
sudo apt-get install libc6 libstdc++6 libkrb5-3 libcurl3 openssl debconf unixodbc unixodbc-dev #install dependencies
sudo dpkg -i msodbcsql_13.1.X.X-X_amd64.deb #install the Driver
```

#### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12
- Загрузите последнюю версию `msodbcsql` `.rpm` отсюда: https://packages.microsoft.com/sles/12/prod/
- Установите зависимости и драйвер

```
zypper install glibc, libuuid1, krb5, openssl, unixODBC unixODBC-devel #install dependencies
sudo rpm -i  msodbcsql-13.1.X.X-X.x86_64.rpm #install the Driver
```

После завершения установки пакета, можно убедиться, что [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 можно найти все его зависимости, запустив ldd и проверка его выходные данные для отсутствующих библиотек:
```
ldd /opt/microsoft/msodbcsql/lib64/libmsodbcsql-*
```
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-linux"></a>Microsoft ODBC Driver for SQL Server версии 11 на Linux

Для использования драйвера сначала установите диспетчер драйверов unixODBC. Дополнительные сведения: [Установка диспетчера драйверов](../../../connect/odbc/linux-mac/installing-the-driver-manager.md).

**Действия по установке**  

> [!IMPORTANT]  
> Эти инструкции ссылаются на `msodbcsql-11.0.2270.0.tar.gz` (файл установки для Red Hat Linux). В случае установке предварительной версии для SUSE Linux файл называется `msodbcsql-11.0.2260.0.tar.gz`.  
  
Порядок установки драйвера

1.  Убедитесь, что у вас есть корневое разрешение.  

2.  Перейдите в каталог, где загрузки поместила файл `msodbcsql-11.0.2270.0.tar.gz`. Убедитесь в наличии файла \*.TAR.GZ, который соответствует вашей версии Linux. Чтобы извлечь файлы, выполните следующую команду: `tar xvzf msodbcsql-11.0.2270.0.tar.gz`.  
  
3.  Перейдите в каталог `msodbcsql-11.0.2270.0`, где должен находиться файл **install.sh**.  
  
4.  Чтобы просмотреть список доступных параметров установки, выполните следующую команду: **./install.sh**.  
  
5.  Создайте резервную копию **odbcinst.ini**. Установка драйвера обновляет **odbcinst.ini**. Файл odbcinst.ini содержит список драйверов, которые зарегистрированы с помощью диспетчера драйверов unixODBC. Чтобы определить на компьютере расположение файла odbcinst.ini, выполните следующую команду: ```odbc_config --odbcinstini```.  
  
6.  Перед установкой драйвера выполните следующую команду: `./install.sh verify`. Выходные данные команды `./install.sh verify` показывают, есть ли на компьютере ПО, необходимое для поддержки драйвера ODBC на Linux.  
  
7.  Когда вы будете готовы установить драйвер ODBC на Linux, выполните команду: `./install.sh install`. Если вам нужно будет дополнительно указать команду установки (`bin-dir` или `lib-dir`), сделайте это после параметра **install**.  
  
8.  После просмотра лицензионного соглашения введите **YES** для продолжения установки.  
  
Установка помещает драйвер `/opt/microsoft/msodbcsql/11.0.2270.0`. Драйвер и его вспомогательные файлы должны находиться в `/opt/microsoft/msodbcsql/11.0.2270.0`.  
  
Для проверки, что драйвер ODBC в Linux зарегистрирован, выполните следующую команду: ```odbcinst -q -d -n "ODBC Driver 11 for SQL Server"```.  
  
В статье[Использование существующих примеров MSDN C++ ODBC для драйвера ODBC в Linux](https://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) показан пример кода, который подключается к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью драйвера ODBC в Linux.  
  
**Удаление**  
  
Вы можете удалить драйвер ODBC 11 на Linux, выполнив следующие команды:  
  
1.  `rm -f /usr/bin/sqlcmd`
  
2.  `rm -f /usr/bin/bcp`  
  
3.  `rm -rf /opt/microsoft/msodbcsql`  
  
4.  `odbcinst -u -d -n "ODBC Driver 11 for SQL Server"`
  
## <a name="troubleshooting-connection-problems"></a>Устранение неполадок с соединениями  
Если установить подключение к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью драйвера ODBC не удается, следующие сведения помогут вам определить проблему.  
  
Наиболее распространенная проблема подключения связана с наличием двух установленных копий диспетчера драйверов UnixODBC. Поищите libodbc\*.so\*в /usr. Если отображается более одной версии файла, (возможно) установлено несколько диспетчеров драйверов. Приложение может использовать неправильную версию.
  
Включите журнал соединений, изменив вашей `/etc/odbcinst.ini` файл, чтобы поместить в следующем разделе, со следующими элементами:

```
[ODBC]
Trace = Yes
TraceFile = (path to log file, or /dev/stdout to output directly to the terminal)
```  
  
Если возникает другой сбой подключения и файл журнала отсутствует, (возможно) на компьютере присутствуют две копии диспетчера драйверов. В противном случае выходные данные журнала должны быть аналогичны следующему:  
  
```  
[ODBC][28783][1321576347.077780][SQLDriverConnectW.c][290]  
        Entry:  
            Connection = 0x17c858e0  
            Window Hdl = (nil)  
            Str In = [DRIVER={ODBC Driver 13 for SQL Server};SERVER={contoso.com};Trusted_Connection={YES};WSID={mydb.contoso.com};AP...][length = 139 (SQL_NTS)]  
            Str Out = (nil)  
            Str Out Max = 0  
            Str Out Ptr = (nil)  
            Completion = 0  
        UNICODE Using encoding ASCII 'UTF8' and UNICODE 'UTF16LE'  
```  
  
В случае если кодировка символов ASCII отличается от UTF-8, например: 
  
```  
UNICODE Using encoding ASCII 'ISO8859-1' and UNICODE 'UCS-2LE'  
```  
  
Имеется более чем один диспетчер драйверов, который приложение использует неправильным, один или диспетчер драйверов не был построен корректно.  
  
Дополнительные сведения об устранении неполадок подключения см. в статьях:  
  
-   [Шаги для устранения неполадок с подключением SQL](https://blogs.msdn.com/b/sql_protocols/archive/2008/04/30/steps-to-troubleshoot-connectivity-issues.aspx)  
  
-   [Устранение проблем с подключением в SQL Server 2005 — часть I](https://blogs.msdn.com/b/sql_protocols/archive/2005/10/22/sql-server-2005-connectivity-issue-troubleshoot-part-i.aspx)  
  
-   [Устранение проблем с подключением в SQL Server 2008 с помощью кольцевого буфера подключения](https://blogs.msdn.com/b/sql_protocols/archive/2008/05/20/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer.aspx)  
  
-   [Средство устранения неполадок проверки подлинности SQL Server](https://blogs.msdn.com/b/sqlsecurity/archive/2010/03/29/sql-server-authentication-troubleshooter.aspx)  
  
-   [Сведения об ошибке (https://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=11001)](https://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=001)  
  
    Номер ошибки, указанный в URL-адресе (11001), следует изменить в соответствии с отображаемой ошибкой.  
  
## <a name="driver-files"></a>Файлы драйвера
Драйвер ODBC для Linux и MacOS состоит из следующих компонентов:

### <a name="linux"></a>Linux

|Компонент|Описание|  
|---------------|-----------------|  
|libmsodbcsql-17. X.so.X.X или libmsodbcsql-13. X.so.X.X|Общий объект (`so`) файла динамической библиотеки, содержащий все функциональные возможности драйвера. Этот файл устанавливается в `/opt/microsoft/msodbcsql17/lib64/` Driver 17 и в `/opt/microsoft/msodbcsql/lib64/` для Driver 13.|  
|`msodbcsqlr17.rll` либо `msodbcsqlr13.rll`|Сопутствующий файл ресурса для библиотеки драйвера. Этот файл устанавливается в `[driver .so directory]../share/resources/en_US/`| 
|msodbcsql.h|Файл заголовка, содержащий все новые определения, необходимые для использования драйвера.<br /><br /> **Примечание**  . Нельзя сослаться на msodbcsql.h и odbcss.h в одной программе.<br /><br /> msodbcsql.h устанавливается в `/opt/microsoft/msodbcsql17/include/` Driver 17 и в `/opt/microsoft/msodbcsql/include/` для Driver 13. |
|LICENSE.txt|Текстовый файл, содержащий условия лицензионного соглашения. Этот файл будет помещен в `/usr/share/doc/msodbcsql17/` Driver 17 и в `/usr/share/doc/msodbcsql/` для Driver 13.|
|RELEASE_NOTES|Текстовый файл, содержащий заметки о выпуске. Этот файл будет помещен в `/usr/share/doc/msodbcsql17/` Driver 17 и в `/usr/share/doc/msodbcsql/` для Driver 13.|


### <a name="macos"></a>MacOS

|Компонент|Описание|  
|---------------|-----------------|  
|libmsodbcsql.17.dylib или libmsodbcsql.13.dylib|Файл динамической библиотеки (`dylib`), содержащий все функциональные возможности драйвера. Этот файл устанавливается в `/usr/local/lib/`.|  
|`msodbcsqlr17.rll` либо `msodbcsqlr13.rll`|Сопутствующий файл ресурса для библиотеки драйвера. Этот файл устанавливается в `[driver .dylib directory]../share/msodbcsql17/resources/en_US/` Driver 17 и в `[driver .dylib directory]../share/msodbcsql/resources/en_US/` для Driver 13. | 
|msodbcsql.h|Файл заголовка, содержащий все новые определения, необходимые для использования драйвера.<br /><br /> **Примечание**  . Нельзя сослаться на msodbcsql.h и odbcss.h в одной программе.<br /><br /> msodbcsql.h устанавливается в `/usr/local/include/msodbcsql17/` Driver 17 и в `/usr/local/include/msodbcsql/` для Driver 13. |
|LICENSE.txt|Текстовый файл, содержащий условия лицензионного соглашения. Этот файл будет помещен в `/usr/local/share/doc/msodbcsql17/` Driver 17 и в `/usr/local/share/doc/msodbcsql/` для Driver 13. |
|RELEASE_NOTES|Текстовый файл, содержащий заметки о выпуске. Этот файл будет помещен в `/usr/local/share/doc/msodbcsql17/` Driver 17 и в `/usr/local/share/doc/msodbcsql/` для Driver 13. |

## <a name="resource-file-loading"></a>Загрузка файла ресурсов

Этот драйвер должен загружать файлы ресурсов для работы. Этот файл называется `msodbcsqlr17.rll` или `msodbcsqlr13.rll` в зависимости от версии драйвера. Расположение `.rll` файл является относительно расположения самого драйвера (`so` или `dylib`), как указано в приведенной выше таблице. Начиная с версии 17.1 драйвер также попытается загрузить `.rll` по умолчанию каталог, если загрузка из относительный путь завершается сбоем. Пути к файлам ресурсов по умолчанию являются:

Linux: `/opt/microsoft/msodbcsql17/share/resources/en_US/`

MacOS: `/usr/local/share/msodbcsql17/resources/en_US/`


  
## <a name="see-also"></a>См. также:

[Установка диспетчера драйверов](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)

[Требования к системе](../../../connect/odbc/linux-mac/system-requirements.md)
