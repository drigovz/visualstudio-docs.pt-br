---
title: 'Como: criar um manifesto do produto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73e2c3f2c9736fd762a9e763827ed641ea5069f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153819"
---
# <a name="how-to-create-a-product-manifest"></a>Como criar um manifesto de produto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para implantar os pré-requisitos para seu aplicativo, você pode criar um pacote de bootstrapper. Um pacote de bootstrapper contém um único arquivo de manifesto de produto, mas um manifesto de pacote para cada localidade. O manifesto do pacote contém aspectos específicos da localização do seu pacote. Isso inclui cadeias de caracteres, contratos de licença de usuário final e pacotes de idiomas.  
  
 Para obter mais informações sobre manifestos de produto, consulte [como criar um manifesto de pacote](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Criando o manifesto do produto  
  
#### <a name="to-create-the-product-manifest"></a>Para criar o manifesto do produto  
  
1. Crie um diretório para o pacote de bootstrapper. Este exemplo usa C:\package.  
  
2. No Visual Studio, crie um novo arquivo XML chamado `product.xml` e salve-o na pasta C:\package.  
  
3. Adicione o XML a seguir para descrever o namespace XML e o código do produto para o pacote. Substitua o código do produto por um identificador exclusivo para o pacote.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4. Adicione XML para especificar que o pacote tem uma dependência. Este exemplo usa uma dependência de Microsoft Windows Installer 3,1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5. Adicione XML para listar todos os arquivos que estão no pacote de bootstrapper. Este exemplo usa o nome do arquivo de pacote CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6. Copie ou mova o arquivo de CorePackage.msi para a pasta C:\package  
  
7. Adicione XML para instalar o pacote usando comandos bootstrapper. O bootstrapper adiciona automaticamente o sinalizador **/qn** ao arquivo. msi, que será instalado silenciosamente. Se o arquivo for um. exe, o bootstrapper executará o arquivo. exe usando o Shell. O XML a seguir mostra nenhum argumento para CorePackage.msi, mas você pode colocar o argumento de linha de comando no atributo Arguments.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8. Adicione o seguinte XML para verificar se esse pacote de bootstrapper está instalado. Substitua o código do produto pelo GUID do componente redistribuível.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Adicione XML para alterar o comportamento do bootstrapper dependendo se o componente do bootstrapper já estiver instalado. Se o componente estiver instalado, o pacote de bootstrapper não será executado. O XML a seguir verifica se o usuário atual é um administrador, pois esse componente requer privilégios administrativos.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Adicione XML para definir códigos de saída se a instalação for bem-sucedida e se uma reinicialização for necessária. O XML a seguir demonstra os códigos de saída de falha e FailReboot, que indicam que o bootstrapper não continuará Instalando pacotes.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Adicione o XML a seguir para encerrar a seção para comandos de bootstrapper.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Mova a pasta C:\package para o diretório do bootstrapper do Visual Studio. Para o Visual Studio 2010, esse é o diretório \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages  
  
## <a name="example"></a>Exemplo  
 O manifesto do produto contém instruções de instalação para pré-requisitos personalizados.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)
