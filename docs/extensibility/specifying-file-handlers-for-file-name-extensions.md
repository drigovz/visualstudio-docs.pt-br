---
title: Especificando manipuladores de arquivo para extensões de nome de arquivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbc85a506b51a29f1c4809890eaeeb0dcecc99a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719575"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Especificando identificadores de arquivo para extensões de nome de arquivo
Há várias maneiras de determinar o aplicativo que manipula um arquivo que tem uma extensão de arquivo específica. Os verbos OpenWithList e OpenWithProgids são duas maneiras de especificar manipuladores de arquivo na entrada do registro para a extensão de arquivo.

## <a name="openwithlist-verb"></a>Verbo OpenWithList
 Ao clicar com o botão direito do mouse em um arquivo no Windows Explorer, você verá o comando **abrir** . Se mais de um produto estiver associado a uma extensão, você verá um submenu **abrir com** .

 Você pode registrar diferentes aplicativos para abrir uma extensão, definindo a chave OpenWithList para a extensão de arquivo em HKEY_CLASSES_ROOT. Os aplicativos listados nessa chave para uma extensão de arquivo aparecem no título **programas recomendados** na caixa de diálogo **abrir com** . O exemplo a seguir mostra os aplicativos registrados para abrir a extensão de arquivo. vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> As chaves que especificam aplicativos são da lista em HKEY_CLASSES_ROOT\Applications.

 Ao adicionar uma chave OpenWithList, você declara que seu aplicativo oferece suporte a uma extensão de arquivo, mesmo que outro aplicativo assuma a propriedade da extensão. Isso pode ser uma versão futura do seu aplicativo ou outro aplicativo.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Identificadores programáticos (ProgIDs) são versões amigáveis do ClassIDs que identificam uma versão de um aplicativo ou objeto COM. Todo objeto creatable deve ter seu próprio ProgID. Por exemplo, VisualStudio. DTE. 7.1 inicia o Visual Studio .NET 2003 enquanto o VisualStudio. DTE. 10.0 inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Como o proprietário de um tipo de projeto ou tipo de item de projeto, você deve criar um ProgID específico de versão para sua extensão de arquivo. Esses ProgIDs podem ser redundantes, pois mais de um ProgID pode iniciar o mesmo aplicativo. Para obter mais informações, consulte [registrando verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md).

 Use a seguinte convenção de nomenclatura para ProgIDs de arquivo com versão para evitar a duplicação com o registro de outros fornecedores:

|Extensão de arquivo|ProgID com versão|
|--------------------|----------------------|
|. extensão|NomeDoProduto. extensão. Propriedade VersionMajor. versionMinor|

 Você pode registrar diferentes aplicativos que podem abrir uma extensão de arquivo específica adicionando ProgIDs com versão como valores para o HKEY_CLASSES_ROOT \\ *\<extension >* chave \OpenWithProgids. Essa chave do registro contém uma lista de ProgIDs alternativos associados à extensão de arquivo. Os aplicativos associados às ProgIDs listados aparecem no submenu **abrir com**_nome do produto_ . Se o mesmo aplicativo for especificado nas chaves `OpenWithList` e `OpenWithProgids`, o sistema operacional mesclará as duplicatas.

> [!NOTE]
> Só há suporte para a chave `OpenWithProgids` no Windows XP. Como outros sistemas operacionais ignoram essa chave, não a use como o único registro para manipuladores de arquivos. Use essa chave para fornecer uma melhor experiência do usuário no Windows XP.

 Adicione as ProgIDs desejadas como valores do tipo REG_NONE. O código a seguir fornece um exemplo de registro de ProgIDs para uma extensão de arquivo (. *ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 O ProgID especificado como o valor padrão para a extensão de arquivo é o manipulador de arquivo padrão. Se você modificar o ProgID de uma extensão de arquivo fornecida com uma versão anterior do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou que possa ser usada por outros aplicativos, deverá registrar a chave de `OpenWithProgids` para a extensão de arquivo e especificar o novo ProgID na lista junto com os ProgIDs antigos  Você dá suporte a. Por exemplo:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Se o ProgID antigo tiver verbos associados a ele, esses verbos também serão exibidos em **abrir com** o *nome do produto* no menu de atalho.

## <a name="see-also"></a>Consulte também
- [Sobre as extensões de nome de arquivo](../extensibility/about-file-name-extensions.md)
- [Registrar verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md)