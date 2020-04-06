---
title: Especificando manipuladores de arquivos para extensões de nome de arquivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699750"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Especificando identificadores de arquivo para extensões de nome de arquivo
Há uma série de maneiras de determinar o aplicativo que lida com um arquivo que tem uma extensão de arquivo particular. Os verbos OpenWithList e OpenWithProgids são duas maneiras de especificar manipuladores de arquivos sob a entrada de registro para a extensão do arquivo.

## <a name="openwithlist-verb"></a>Verbo abertocomlista
 Ao clicar com o botão direito do mouse em um arquivo no Windows Explorer, você verá o comando **Abrir.** Se mais de um produto estiver associado a uma extensão, você verá um **submenu Aberto com.**

 Você pode registrar diferentes aplicativos para abrir uma extensão definindo a tecla OpenWithList para a extensão de arquivo em HKEY_CLASSES_ROOT. Os aplicativos listados nesta chave para uma extensão de arquivo aparecem sob o título **Programas Recomendados** na caixa **Abrir com** a caixa de diálogo. O exemplo a seguir mostra os aplicativos registrados para abrir a extensão de arquivo .vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> As chaves especificando aplicativos são da lista em HKEY_CLASSES_ROOT\Aplicativos.

 Ao adicionar uma chave OpenWithList, você declara que seu aplicativo suporta uma extensão de arquivo mesmo que outro aplicativo assuma a propriedade da extensão. Esta pode ser uma versão futura do seu aplicativo ou outro aplicativo.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Identificadores programáticos (ProgIDs) são versões amigáveis dos ClassIDs que identificam uma versão de um aplicativo ou objeto COM. Cada objeto co-creatable deve ter seu próprio ProgID. Por exemplo, o VisualStudio.DTE.7.1 inicia o Visual Studio .NET 2003 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]enquanto o VisualStudio.DTE.10.0 inicia . Como proprietário de um tipo de projeto ou tipo de item de projeto, você deve criar um ProgID específico da versão para sua extensão de arquivo. Esses ProgIDs podem ser redundantes porque mais de um ProgID pode iniciar a mesma aplicação. Para obter mais informações, consulte ['Registrando verbos para extensões de nome de arquivo ''](../extensibility/registering-verbs-for-file-name-extensions.md)

 Use a seguinte convenção de nomeação para ProgIDs de arquivo em versão para evitar a duplicação com registro de outros fornecedores:

|Extensão de arquivo|ProgID versionado|
|--------------------|----------------------|
|.extensão|Productname. extension.versionMajor.versionMinor|

 Você pode registrar diferentes aplicativos que são capazes de abrir uma extensão de\\arquivo específica adicionando ProgIDs versados como valores à*\<extensão *HKEY_CLASSES_ROOT>\OpenWithProgids key. Esta chave de registro contém uma lista de ProgIDs alternativos associados à extensão do arquivo. Os aplicativos associados aos ProgIDs listados aparecem no submenu **Open With**_Product Name._ Se o mesmo aplicativo for `OpenWithList` especificado nas teclas e `OpenWithProgids` nas teclas, o sistema operacional mescla as duplicatas.

> [!NOTE]
> A `OpenWithProgids` chave só é suportada no Windows XP. Como outros sistemas operacionais ignoram essa chave, não a use como o único registro para manipuladores de arquivos. Use esta chave para fornecer uma melhor experiência de usuário no Windows XP.

 Adicione os ProgIDs desejados como valores do tipo REG_NONE. O código a seguir fornece um exemplo de registro de ProgIDs para uma extensão de arquivo (.* ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 O ProgID especificado como o valor padrão para a extensão do arquivo é o manipulador de arquivos padrão. Se você modificar o ProgID para uma extensão [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de arquivo enviada com uma versão anterior ou `OpenWithProgids` que pode ser assumida por outros aplicativos, então você deve registrar a chave para a sua extensão de arquivo e especificar o novo ProgID na lista, juntamente com os ProgIDs antigos que você suporta. Por exemplo:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Se o ProgID antigo tiver verbos associados a ele, esses verbos também aparecerão em **Open With** *Product Name* no menu de atalho.

## <a name="see-also"></a>Confira também
- [Sobre as extensões de nome de arquivo](../extensibility/about-file-name-extensions.md)
- [Registrar verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md)
