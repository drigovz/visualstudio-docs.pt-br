---
title: Como atualizar modelos existentes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b56cf11057957b0eb99fc065ed26af10d8adfbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670582"
---
# <a name="how-to-update-existing-templates"></a>Como atualizar modelos existentes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Depois de criar um modelo e compactar os arquivos em um arquivo .zip, modifique o modelo. É possível fazer isso alterando manualmente os arquivos no modelo ou exportando um novo modelo de um projeto com base no modelo.

## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Usando o Assistente de Exportação de Modelo para atualizar um modelo existente
 O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornece um assistente **Exportar Modelo** que pode ser usado para atualizar um modelo existente.

#### <a name="to-use-export-template-to-update-an-existing-template"></a>Para usar o Assistente Exportar Modelo para atualizar um modelo existente

1. No menu **Arquivo**, clique em **Novo** e, em seguida, clique em **Novo Projeto**.

2. Selecione o modelo que você deseja atualizar, insira um nome e local para seu projeto temporário e clique em **OK**.

3. Modifique o projeto em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. No menu **Arquivo**, clique em **Exportar Modelo** e use o assistente **Exportar Modelo** para criar um novo modelo.

5. Depois que o modelo atualizado for compactado em um arquivo .zip, exclua o arquivo .zip do modelo antigo.

## <a name="manually-updating-an-existing-template"></a>Atualizando manualmente um modelo existente
 É possível atualizar um modelo existente fora do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modificando os arquivos no arquivo .zip compactado.

#### <a name="to-manually-update-an-existing-template"></a>Para atualizar manualmente um modelo existente

1. Localize o arquivo .zip que contém o modelo. Por padrão, esse arquivo está localizado em \Meus Documentos\Visual Studio *Versão*\My Exported Templates\\.

2. Extraia o arquivo .zip.

3. Modifique ou exclua os arquivos de modelo atuais ou adicione novos arquivos ao modelo.

4. Abra, modifique e salve o arquivo XML .vstemplate para tratar o comportamento atualizado ou novos arquivos. Para obter mais informações sobre o esquema .vstemplate, consulte [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Para obter mais informações sobre o que é possível parametrizar nos arquivos de origem, consulte [Parâmetros de modelo](../ide/template-parameters.md)

5. Selecione os arquivos no seu modelo, clique com o botão direito do mouse, clique em **Enviar Para** e, em seguida, clique em **Pasta Compactada (Zipada)**. Os arquivos selecionados são compactados em um arquivo .zip.

6. Coloque o novo arquivo .zip no mesmo diretório do antigo arquivo .zip.

7. Exclua os arquivos de modelo extraídos e o arquivo .zip de modelo antigo.

8. Inicie (como administrador) uma instância do Prompt de Comando do Desenvolvedor (no menu Iniciar, em **Visual Studio 2010/Ferramentas do Visual Studio/Prompt de Comando do Desenvolvedor**).

9. Execute o seguinte comando: `devenv /installvstemplates`.

## <a name="see-also"></a>Consulte Também
 [Personalizando modelos](../ide/customizing-project-and-item-templates.md) [criando modelos de projeto e itens modelo de referência de](../ide/creating-project-and-item-templates.md) [esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md) [Template Parameters](../ide/template-parameters.md) [como criar kits de início](../ide/how-to-create-starter-kits.md)
