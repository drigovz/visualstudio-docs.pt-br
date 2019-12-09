---
title: 'Como: empacotar manualmente uma extensão (implantação do VSIX) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: a615aea75ec00e49ee4d2837b8b4e2b1d20d3306
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293624"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Como: empacotar manualmente uma extensão (implantação do VSIX)
Você pode criar um pacote VSIX para encapsular uma extensão de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para implantação. Há três maneiras de criar o pacote:  
  
- Crie um projeto de pacote VSIX usando um dos modelos de extensibilidade incluídos no SDK do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Essa é a opção mais fácil para a maioria dos cenários.  
  
- Empacote a saída do projeto de extensão em um [projeto VSIX](../extensibility/vsix-project-template.md)vazio. Recomendamos essa opção para modelos, assemblies sem suporte e tipos personalizados.  
  
- Crie manualmente um pacote VSIX. Recomendamos essa opção somente quando as outras duas opções não estiverem disponíveis.  
  
  Este documento descreve a terceira opção.  
  
## <a name="creating-a-vsix-package"></a>Criando um pacote VSIX  
 Para empacotar manualmente uma extensão, adicione um arquivo de extensão. manifest e um arquivo [Content_Types]. xml ao projeto de extensão, coloque-os em um arquivo compactado junto com a saída de compilação e renomeie o arquivo compactado para que ele tenha uma extensão de nome de arquivo. vsix. A extensão a ser empacotada deve ser de um tipo com suporte pelo [esquema VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
> Os nomes de arquivos em pacotes VSIX não devem incluir espaços, nem caracteres reservados em identificadores de recursos uniformes (URI), conforme definido em [\[RFC2396\]](https://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### <a name="to-manually-create-a-vsix-package"></a>Para criar manualmente um pacote VSIX  
  
1. Crie uma extensão do Visual Studio de um tipo com suporte no esquema VSIX.  
  
2. Crie um arquivo XML e nomeie-o `extension.vsixmanifest`.  
  
3. Preencha o arquivo extension. vsixmanifest de acordo com o esquema VSIX. Para obter um exemplo de manifesto, consulte [elemento PackageManifest (elemento raiz, esquema VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4. Crie um segundo arquivo XML e nomeie-o `[Content_Types].xml`.  
  
5. Preencha o arquivo [Content_Types]. XML conforme especificado na [estrutura do arquivo Content_types\]. xml](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
6. Coloque ambos os arquivos XML em um diretório junto com a extensão a ser implantada.  
  
     No caso de um modelo de projeto ou modelo de item, coloque o arquivo. zip que contém o modelo na mesma pasta que os arquivos XML. Não coloque os arquivos XML no arquivo. zip.  
  
     Em todos os outros casos, coloque os arquivos XML no mesmo diretório que a saída da compilação.  
  
7. No Windows Explorer, clique com o botão direito do mouse na pasta que contém o conteúdo da extensão e os dois arquivos XML, clique em **Enviar para**e clique em **pasta compactada (zipada)** .  
  
8. Renomeie o arquivo. zip resultante para *filename*. vsix, em que *filename* é o nome do arquivo redistribuível que instala o pacote.  
  
## <a name="see-also"></a>Consulte também  
 [Enviando  de extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)  
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Elemento PackageManifest (elemento raiz, esquema VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)