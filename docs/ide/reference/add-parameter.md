---
title: Adicionar parâmetro a uma ação rápida de método
ms.date: 09/28/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3e1461afe5c4d6026f8532896ba837e971fed652
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62792249"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Adicionar um parâmetro a um método usando uma Ação Rápida

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** Permite adicionar automaticamente um parâmetro a um método com base no uso.

**Quando:** Você precisa adicionar um parâmetro a um método e deseja declará-lo automaticamente.

**Por que:** Você poderia adicionar o parâmetro para a declaração do método antes de chamá-lo, no entanto, esse recurso adiciona o parâmetro automaticamente com base na chamada de método.

## <a name="how-to-use-it"></a>Como usá-lo

1. Adicione um argumento extra a uma chamada de método.

   Uma linha vermelha "ondulada" aparece sob o nome do método onde você o chama.

2. Coloque o ponteiro sobre a linha vermelha "ondulada" até aparecer o menu Ações rápidas. Selecione a **seta para baixo** no menu Ações Rápidas e, em seguida, selecione **Adicionar parâmetro ao [método]**.

   ![Adicionar parâmetro a ação rápida de método no Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > Também é possível acessar o menu Ações Rápidas colocando o cursor na linha de chamada de método e, em seguida, pressionando a tecla **Ctrl**+**.** ou selecionando o ícone de lâmpada na margem de arquivo.

   O Visual Studio adiciona o novo parâmetro à declaração de método.

> [!NOTE]
> Se você tiver outras chamadas para o método, elas podem produzir erros depois de usar essa Ação Rápida porque não especificam um argumento para o parâmetro recém-adicionado.

## <a name="see-also"></a>Consulte também

- [Adicionar parâmetro ao construtor](generate-constructor.md#addparameter)