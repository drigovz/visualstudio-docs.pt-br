---
title: 'Como: Criar um manifesto de pacote | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8083ca9a8d3025b1760edde96279a0cd557f722
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899734"
---
# <a name="how-to-create-a-package-manifest"></a>Como: Criar um manifesto do pacote
Para implantar o pré-requisitos para o seu aplicativo, você pode usar um pacote de bootstrapper. Um pacote de bootstrapper contém um arquivo de manifesto de produto único, mas um manifesto de pacote para cada localidade. Funcionalidade compartilhada entre diferentes versões localizadas deve ir para o manifesto do produto.

 Para obter mais informações sobre manifestos de produto, consulte [como: Criar um manifesto de produto](../deployment/how-to-create-a-product-manifest.md).

## <a name="create-the-package-manifest"></a>Crie o manifesto de pacote

#### <a name="to-create-the-package-manifest"></a>Para criar o manifesto do pacote

1. Crie um diretório para o pacote de bootstrapper. Este exemplo usa *C:\package*.

2. Crie um subdiretório com o nome da localidade, como *en* para inglês.

3. No Visual Studio, crie um arquivo XML que é denominado *Package. XML*e salvá-lo para o *C:\package\en* pasta.

4. Adicione o XML para listar o nome do pacote de bootstrapper, a cultura para esse manifesto de pacote localizado e o contrato de licença opcional. O XML a seguir usa as variáveis `DisplayName` e `Culture`, que é definido em um elemento posterior.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Adicione o XML para listar todos os arquivos que estão no diretório específica de localidade. O XML a seguir usa um arquivo chamado *EULA* que é aplicável para o **en** localidade.

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Adicione o XML para definir as cadeias de caracteres localizáveis para o pacote de bootstrapper. O XML a seguir adiciona cadeias de caracteres de erro para o **en** localidade.

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. Cópia de *C:\package* pasta para o diretório de bootstrapper do Visual Studio. Para o Visual Studio 2010, este é o *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* directory.

## <a name="example"></a>Exemplo
 O manifesto de pacote contém informações específicas de localidade, como mensagens de erro, termos de licença de software e pacotes de idiomas.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.txt">

  <PackageFiles>
    <PackageFile Name="eula.txt"/>
  </PackageFiles>

  <Strings>
    <String Name="DisplayName">Custom Bootstrapper Package</String>
    <String Name="Culture">en</String>
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>
    <String Name="GeneralFailure">A general error has occurred while
installing this package.</String>
  </Strings>
</Package>
```

## <a name="see-also"></a>Consulte também
- [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)