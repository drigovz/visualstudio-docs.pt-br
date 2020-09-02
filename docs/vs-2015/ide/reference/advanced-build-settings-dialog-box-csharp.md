---
title: Caixa de diálogo Configurações de Build Avançadas (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38f4d233c8804bec91d2f7dfd2dc34c6879e8be9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651730"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Caixa de diálogo Configurações de Build Avançadas (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use a caixa de diálogo **Configurações de Build Avançadas** do **Designer de Projeto** para especificar as propriedades de configuração de build avançadas do projeto. Essa caixa de diálogo se aplica somente a projetos [!INCLUDE[csprcs](../../includes/csprcs-md.md)].

## <a name="general"></a>Geral
 As opções a seguir permitem definir configurações gerais avançadas.

 **Versão da Linguagem** Especifica a versão da linguagem a ser usada. O conjunto de recursos é diferente em cada versão e, portanto, essa opção pode ser usada para forçar o compilador a permitir somente um subconjunto dos recursos implementados ou permitir somente os recursos compatíveis com um padrão existente. Essa configuração tem as seguintes opções:

- **ISO-1**

   Tem como destino os recursos padrão ISO-1.

- **default**

   Define a versão atual como destino.

  Para obter mais informações, consulte [/langversion (opções do compilador C#)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).

  **Relatório de erros do compilador interno** Especifica se os erros do compilador são relatados à Microsoft. Se for definido como **prompt** (o padrão), você receberá um prompt se ocorrer um erro interno do compilador, fornecendo a opção de enviar um relatório de erro eletronicamente à Microsoft. Se for definido como **send**, um relatório de erros será enviado automaticamente. Se for definido como **queue**, relatórios de erros serão colocados na fila. Se for definido como **none**, o erro será relatado somente na saída de texto do compilador. Para obter mais informações, consulte [/errorreport (opções do compilador C#)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).

  **Verificar estouro/Subfluxo aritmético** Especifica se uma instrução aritmética de inteiro que não está no escopo das palavras [-chave verificadas](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) ou [desmarcadas](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) e que resulta em um valor fora do intervalo do tipo de dados causará uma exceção em tempo de execução. Para obter mais informações, consulte [/Checked (opções do compilador C#)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).

  **Não referenciar mscorlib.dll** Especifica se mscorlib.dll será importado para o programa, definindo todo o namespace <xref:System>. Marque essa caixa se desejar definir ou criar seus próprios objetos e namespace <xref:System>. Para obter mais informações, consulte [/nostdlib (opções do compilador C#)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).

## <a name="output"></a>Saída
 As opções a seguir permitem especificar opções de saída avançadas.

 **Informações de depuração** Especifica o tipo de informações de depuração geradas pelo compilador. Para obter informações sobre como configurar o desempenho de depuração de um aplicativo, consulte [Facilitando a depuração de uma imagem](https://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Essa configuração tem as seguintes opções:

- **nenhum**

   Especifica que nenhuma informação de depuração será gerada

- **completo**

   Permite anexar um depurador ao programa em execução.

- **pdbonly**

   Permite a depuração de código-fonte quando o programa é iniciado no depurador, mas apenas exibirá o assembler quando o programa em execução estiver anexado ao depurador.

  Para obter mais informações, consulte [/debug (opções do compilador C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).

  **Alinhamento de arquivo** Especifica o tamanho das seções no arquivo de saída. Os valores válidos são **512**, **1024**, **2048**, **4096**e **8192**. Esses valores são medidos em bytes. Cada seção será alinhada em um limite que é um múltiplo desse valor, afetando o tamanho do arquivo de saída. Para obter mais informações, consulte [/filealign (opções do compilador C#)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).

  **Endereço básico de dll** Especifica o endereço base preferencial no qual carregar uma DLL. O endereço básico padrão para uma DLL é definido pelo Common Language Runtime de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Para obter mais informações, consulte [/BaseAddress (opções do compilador C#)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).

## <a name="see-also"></a>Consulte Também
 [Opções do Compilador C#](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44) [Página de Build, Designer de Projeto (C#)](../../ide/reference/build-page-project-designer-csharp.md)
