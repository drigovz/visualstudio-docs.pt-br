---
title: Anatomia de um pacote VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 156b221265b4c3c23b795b09b9a50ccb27a63bcf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295650"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia de um pacote do VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um pacote VSIX é um arquivo. vsix que contém uma ou mais extensões do Visual Studio, junto com os metadados que o Visual Studio usa para classificar e instalar as extensões. Esses metadados estão contidos no manifesto do VSIX e no arquivo [Content_Types]. xml. Um pacote VSIX também pode conter um ou mais arquivos Extension. vsixlangpack para fornecer texto de instalação localizado e pode conter pacotes VSIX adicionais para instalar dependências.  
  
 O formato do pacote VSIX segue o padrão OPC (Open Packaging Conventions). O pacote contém binários e arquivos de suporte, juntamente com um arquivo [Content_Types]. xml e um arquivo de manifesto. vsix. Um pacote VSIX pode conter a saída de vários projetos ou até mesmo vários pacotes que têm seus próprios manifestos.  
  
> [!NOTE]
> Os nomes dos arquivos incluídos nos pacotes VSIX não devem incluir espaços, nem caracteres reservados em identificadores de recursos uniformes (URI), conforme definido em [\[RFC2396\]](https://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>O manifesto do VSIX  
 O manifesto do VSIX contém informações sobre a extensão a ser instalada e segue o esquema VSX. Para obter mais informações, consulte [referência do esquema de extensão do VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Para obter um exemplo de manifesto do VSIX, consulte [elemento PackageManifest (elemento raiz, esquema VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 O manifesto do VSIX deve ser nomeado `extension.vsixmanifest` quando ele é incluído em um arquivo. vsix.  
  
## <a name="the-content"></a>O conteúdo  
 Um pacote VSIX pode conter modelos, itens de caixa de ferramentas, VSPackages ou qualquer outro tipo de extensão com suporte no Visual Studio.  
  
## <a name="language-packs"></a>Pacotes de Idiomas  
 Um pacote VSIX pode conter uma ou mais arquivos Extension. vsixlangpack para fornecer texto localizado durante a instalação. Para obter mais informações, consulte [localizando pacotes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Dependências e referências  
 Um pacote VSIX pode conter outros pacotes VSIX como referências. Cada um desses outros pacotes deve incluir seu próprio manifesto do VSIX.  
  
 Se um usuário tentar instalar uma extensão que tenha dependências, o instalador verificará se os assemblies necessários estão instalados no sistema do usuário. Se os assemblies necessários não forem encontrados, **as extensões e as atualizações** exibirão uma lista dos assemblies ausentes.  
  
 Se o manifesto de extensão incluir um ou mais elementos de [referência](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) , **as extensões e as atualizações** compararão o manifesto de cada referência às extensões instaladas no sistema e instalará a extensão referenciada se ela ainda não estiver instalada. Se uma versão anterior de uma extensão referenciada for instalada, a versão mais recente a substituirá.  
  
 Se um projeto em uma solução de vários projetos incluir uma referência a outro projeto na mesma solução, o pacote VSIX incluirá as dependências desse projeto. Você pode substituir esse comportamento clicando na referência para o projeto interno e, em seguida, na janela **Propriedades** , definindo os **grupos de saída incluídos na propriedade VSIX** como `BuiltProjectOutputGroup`.  
  
 Para incluir DLLs satélite de assemblies referenciados no pacote VSIX, adicione `SatelliteDllsProjectOutputGroup` aos **grupos de saída incluídos na propriedade VSIX** .  
  
## <a name="installation-location"></a>Local de instalação  
 Durante a instalação, **as extensões e as atualizações** do buscam o conteúdo do pacote do VSIX em uma pasta em%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Por padrão, a instalação se aplica somente ao usuário atual, pois% LocalAppData% é um diretório específico do usuário. No entanto, se você definir o elemento [AllUsers](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) do manifesto como `True`, a extensão será instalada em..\\*VisualStudioInstallationFolder*\Common7\IDE\Extensions e estará disponível para todos os usuários do computador.  
  
## <a name="content_typesxml"></a>[Content_Types]. xml  
 O arquivo [Content_Types]. xml identifica os tipos de arquivo no arquivo. vsix expandido. O Visual Studio usa esse arquivo durante a instalação do pacote, mas não instala o próprio arquivo. Para obter mais informações sobre esse arquivo, consulte [a estrutura do arquivo Content_types\]. xml](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
 Um arquivo [Content_Types]. xml é exigido pelo padrão OPC (Open Packaging Conventions). Para obter mais informações sobre o OPC, consulte [OPC: um novo padrão para empacotar seus dados](https://go.microsoft.com/fwlink/?LinkID=148207) no site do MSDN.
