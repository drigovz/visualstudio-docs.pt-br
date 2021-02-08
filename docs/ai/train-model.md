---
title: Enviar um trabalho para treinar um modelo
description: Enviar um trabalho para treinar um modelo usando a ia do lote do Azure
ms.custom: SEO-VS-2020
keywords: ia, visual studio, modelo de treinamento, nuvem
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: e1bb1d0bde1b564fe9a35f3527c7b3803c7e9d78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841296"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Treinar modelos de IA no Lote do Azure AI

A IA do Lote é um serviço gerenciado que permite que os pesquisadores de IA e cientistas de dados treinem IA e outros modelos de aprendizado de máquina em clusters de máquinas virtuais do Azure, incluindo VMs com suporte de GPU. Descreva os requisitos do seu trabalho, onde encontrar as entradas e armazenar as saídas, e a IA do Lote cuida do resto. [Saiba mais sobre a IA do Lote do Azure](/azure/batch-ai/overview)

Ela está integrada às Ferramentas do Visual Studio para IA, assim, é possível aumentar de forma dinâmica modelos de treinamento no Azure.  Depois de [instalar as Ferramentas do Visual Studio para IA](installation.md), é fácil criar um novo projeto Python usando receitas predefinidas na galeria de exemplos do Azure Machine Learning.

1. Inicie o Visual Studio. Abra o **Gerenciador de Servidores** abrindo o menu **Ferramentas de IA** e escolhendo **Selecionar Cluster**

    ![Seletor de cluster](media/train-model/select-cluster.png)

2. Expanda **Ferramentas de IA**. Todos os recursos do IA do Lote serão detectados automaticamente e exibidos no Gerenciador de Servidores.

    ![Captura de tela da árvore de pastas expandida para ferramentas de ia no Gerenciador de Servidores, mostrando subpastas expandidas para ia e Azure Machine Learning do lote do Azure.](media/train-model/batchai.png)

3. Selecione **Exibir > Team Explorer...** para abrir a janela do **Team Explorer**, em que é possível se conectar ao GitHub ou ao Azure DevOps ou clonar um repositório.

    ![Janela do Team Explorer mostrando o Azure DevOps, o GitHub e a clonagem de um repositório](media/train-model/team-explorer-devops.png)

4. No campo de URL em **Repositórios Git Locais**, insira `https://github.com/Microsoft/samples-for-ai`, insira uma pasta para os arquivos clonados e selecione **Clonar**.

    > [!Tip]
    > A pasta especificada no Team Explorer é a pasta específica para receber os arquivos clonados. Ao contrário do comando `git clone`, criar um clone no Team Explorer não cria automaticamente uma subpasta com o nome do repositório.

5. Quando a clonagem for concluída, clique em **Arquivo > Abrir Solução > Projeto/Solução**

    ![Captura de tela mostrando parte do menu Gerenciador de Servidores Arquivo com o comando abrir selecionado e projeto/solução selecionado no menu de contexto.](media/train-model/open-solution.png)

6. Abra **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** no diretório em que o repositório foi clonado

    ![Captura de tela mostrando o arquivo de solução TensorflowExamples. sln listado no conteúdo da pasta TensorflowExamples no repositório Samples for ai.](media/train-model/tensorflowexamples.png)

7. Defina o projeto do MNIST como o **Projeto de Inicialização**

    ![Captura de tela mostrando definir como projeto de inicialização selecionado no menu de contexto do projeto MNIST no Gerenciador de Soluções.](media/train-model/mnist-startup.png)

8. <strong>Clique com o botão direito do mouse no **projeto do MNIST e clique em** **Enviar Trabalho**</strong>

    ![Captura de tela mostrando trabalho de envio selecionado no menu de contexto do projeto MNIST no Gerenciador de Soluções.](media/train-model/submit-job.png)
9. Selecione o cluster da **IA do Lote do Azure** e, depois, clique em **Importar**. Selecione o arquivo `AzureBatchAI_TF_MNIST.json` para preencher rapidamente alguns valores padrão, como qual imagem do Docker usar. Então clique em **Enviar**

    ![Captura de tela da caixa de diálogo Enviar trabalho com valores populados para usar cluster, script de inicialização, nome do trabalho, nome da imagem, prefixo de caminho StdOutErr e parâmetros da CLI.](media/train-model/submit-batch.png)
