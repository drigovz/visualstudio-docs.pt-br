---
title: 'Como: Criar um pacote de Bootstrapper localizado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 856ea1e59a32a64c6a48b52c3ef1dcad9e0bbb80
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406840"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Como: Criar um pacote de bootstrapper localizado
Depois de criar um pacote de bootstrapper, você pode criar versões localizadas desse pacote criando mais dois arquivos para cada localidade: um arquivo de termos de licença de software (como um *eula.rtf*) e um manifesto do pacote (*package.xml*).

 Por padrão, o Visual Studio 2010 inclui pacotes de bootstrapper localizados apenas para os .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 e F# Runtime 4.0. Você pode criar pacotes localizados para outros bootstrappers concluindo três etapas.

1. Crie uma pasta que é nomeada após o nome da localidade na *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<Nomepacotebootstrapper >*.

2. Crie um arquivo que contém os termos de licença de software para o pacote de bootstrapper e coloque-o na nova pasta.

3. Crie um manifesto do pacote com o nome *package.xml*, atualize as cadeias de caracteres e cultura e coloque o arquivo na nova pasta. Se você já criou um bootstrapper do Visual Studio no idioma de destino, você pode copiar o arquivo *package.xml* do Visual Studio e modificá-lo nesta etapa.

> [!NOTE]
> Se você estiver usando um projeto de instalação para implantar aplicativos, você poderá localizar o aplicativo alterando a propriedade **Localização**.

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Para criar um pacote de bootstrapper localizado

1. Crie uma pasta com o nome da localidade.

     Em computadores de 32 bits, crie a pasta na *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<Nomepacotebootstrapper >\\*  pasta.

     Em computadores de 64 bits, crie a pasta na *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<Nomepacotebootstrapper >\\*  pasta.

     A tabela a seguir mostra os nomes das pastas que você pode usar para estabelecer uma localidade correspondente.

    |Localidade|Nome da pasta|
    |------------|-----------------|
    |Chinês (simplificado)|zh-Hans|
    |Chinês (tradicional)|zh-Hant|
    |Tcheco|cs|
    |Alemão|de|
    |Inglês|en|
    |Espanhol|es|
    |Francês|fr|
    |Italiano|it|
    |Coreano|ko|
    |Japonês|ja|
    |Polonês|pl|
    |Português (Brasil)|pt-BR|
    |Russo|ru|
    |Turco|tr|

2. Crie um arquivo que contém os termos de licença de software para o pacote de bootstrapper e coloque-o na nova pasta.

3. Crie um manifesto do pacote com o nome *package.xml* e coloque-o na nova pasta. Para obter mais informações, confira [Como: Criar um manifesto do pacote](../deployment/how-to-create-a-package-manifest.md).

4. Atualize a seção `<Strings>` do manifesto do pacote, para que as cadeias de caracteres fiquem no idioma correto para a localidade.

5. Altere o valor `<String Name="Culture">` para corresponder ao nome da pasta.

6. Salve o arquivo *package.xml*.

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Para criar um pacote de bootstrapper para o .NET Framework 3.5 Service Pack 1 localizado em francês

1. Crie uma pasta com o nome *fr*. O nome da pasta deve corresponder ao nome da localidade.

     Em computadores de 32 bits, crie a pasta dentro da pasta *\Arquivos de Programas\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Pacotes\DotNetFX35SP1\\\*.

     Em computadores de 64 bits, crie a pasta dentro da pasta *\Arquivos de Programas (86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Pacotes\DotNetFX35SP1\\\*.

2. Coloque uma versão localizada dos termos de licença de software na pasta *fr*.

3. Copie o arquivo *\Arquivos de Programas (x86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Pacotes\DotNetFX35SP1\en\package.xml* para a pasta *fr* e abra-o no XML Designer.

4. Atualize a seção `<Strings>` do pacote do manifesto para que as cadeias de caracteres de erro fiquem em francês.

5. Altere o valor de `<String Name="Culture">` para *fr*.

6. Salve o arquivo *package.xml*.

## <a name="see-also"></a>Consulte também
- [Criar pacotes de bootstrapper](../deployment/creating-bootstrapper-packages.md)
- [Pré-requisitos de implantação do aplicativo](../deployment/application-deployment-prerequisites.md)
- [Como: Criar um manifesto do pacote](../deployment/how-to-create-a-package-manifest.md)