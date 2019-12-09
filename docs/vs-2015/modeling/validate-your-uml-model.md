---
title: Validar seu modelo UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dfaf19e358d96b7737b06880d6fa4581b5c54f8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659369"
---
# <a name="validate-your-uml-model"></a>Validar o modelo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alguns dos modelos UML que você pode desenhar no Visual Studio podem ser considerados inválidos em seu projeto. Por exemplo, você pode exigir que um caso de uso sempre deva ser vinculado a um diagrama de sequência que tem linhas de vida que representam os atores do caso de uso. Você pode instalar ou definir *restrições* que ajudam sua equipe a se adequar aos requisitos como esse. As restrições podem ser aplicadas quando o usuário salva ou abre um modelo e pode ser invocado pelo comando de menu.

 Nenhuma restrição é fornecida com [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], pois elas dependem de como sua equipe interpreta e usa modelos UML. Mas você pode definir suas próprias restrições e instalar restrições que são definidas por outros usuários. Para saber como definir restrições e empacotá-las para distribuição, consulte [definir restrições de validação para modelos UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="invoking-validation"></a>Invocando validação
 Quando você tiver instalado uma extensão de validação, as restrições que ela fornece poderão ser aplicadas nos casos a seguir. Algumas restrições são definidas para aplicar em apenas alguns desses casos.

- **Comando de validação.** Para invocar a validação a qualquer momento, clique em **validar modelo UML** no menu **arquitetura** .

  > [!NOTE]
  > O comando será exibido somente se as restrições de validação estiverem instaladas.

- **Ao salvar um modelo.** Restrições de validação podem ser aplicadas quando você salva o modelo. A finalidade dessas restrições é ajudar a garantir que você não salve um modelo inválido de acordo com a interpretação do projeto.

   Se houver erros, você será perguntado se ainda deseja salvar o modelo. Você pode optar por corrigir os erros ou salvar o modelo de qualquer maneira.

- **Ao abrir um modelo.** Quando você abre um modelo, os métodos de validação podem ser aplicados para restaurar mensagens de erro que existiam quando você salvou o modelo. Os erros também podem ser introduzidos por inconsistências entre as alterações feitas por usuários que trabalham em diferentes partes de um modelo. Para obter mais informações, consulte [compartilhar modelos e exportar diagramas](../modeling/share-models-and-exporting-diagrams.md).

  Erros de validação são relatados na janela [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erros.

  Para selecionar em um diagrama os elementos que estão incorretos, clique duas vezes no erro. Isso só funcionará se os elementos incorretos estiverem visíveis em um diagrama aberto.

## <a name="installing-validation-constraints"></a>Instalando restrições de validação
 As restrições são empacotadas dentro de arquivos de VSIX (extensão de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]). Normalmente, um conjunto de restrições fará parte de uma extensão que também contém outras definições, como comandos de menu, perfis e itens da caixa de ferramentas.

#### <a name="to-install-a-visual-studio-extension"></a>Para instalar uma extensão do Visual Studio

1. Clique duas vezes no arquivo **. vsix** no Windows Explorer (ou explorador de arquivos).

2. Reinicie qualquer instância do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que já esteja em execução.

## <a name="disabling-and-uninstalling-validation-constraints"></a>Desabilitando e desinstalando restrições de validação
 Quando você deseja trabalhar com um modelo ao qual as restrições não se aplicam, você pode desabilitar temporariamente a extensão que as contém. Dessa forma, você pode trabalhar com tipos diferentes de modelo em momentos diferentes, habilitando e desabilitando extensões diferentes.

#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Para desabilitar ou desinstalar uma extensão do Visual Studio

1. No menu **ferramentas** do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], clique em **extensões e atualizações**.

2. Ao lado da extensão, clique em **desabilitar** para desabilitar temporariamente a extensão. Você pode reabilitá-lo mais tarde retornando para a janela **extensões e atualizações** .

     \- ou -

     Clique em **desinstalar** para remover a extensão.

3. Reinicie o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="see-also"></a>Consulte também
 [Definir restrições de validação para modelos UML](../modeling/define-validation-constraints-for-uml-models.md) [criar modelos para seus](../modeling/create-models-for-your-app.md) [modelos de uso de aplicativo em seu processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)
