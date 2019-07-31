---
title: Using intent classifier with Enterprise Graph by Microsoft
description: Learn how to use intent classifier with Enterprise Graph by Microsoft
author: microsteve

ms.service: enterprise-graph
ms.topic: tutorial
ms.date: 05/01/2019
ms.author: stflanag
---

# Tutorial: Create an intent classifier model

In this tutorial, you'll learn to:

> [!div class="checklist"]
> * Add an intent
> * Add an utterance
> * Train, validate, and publish the model
> * Check the history of models
> * Manage customerized tags

## Prerequisites

- Have completed all the essential steps to build the graph.
- Get familiar with the basic [concepts of intent classifier](intent-classifier-overview.md)

## Add an intent

If you have not previously created any intents, you will see an icon along with a short instruction message inviting you to add your first intent, as shown in the window:

![No intents](./media/intent-classifier-tutorial/no-intents-message.png)

Click on the 'Add intent' button, and you will see a panel window launched from right side:

![New intent](./media/intent-classifier-tutorial/add-intent.png)

**Intent:** The meaningful name for the intent.

**This is an Enterprise Graph intent:** The checkbox is selected by default, which means the intent is querying an existing type in the graph.

**Output type (query level):** The output type of this intent, that is, the entity type in the graph, which is referred by the intent.

After you finished all the required fields and click on the "OK" button at bottom, the new intent will show up in a grid as below:

![Intents grid](./media/intent-classifier-tutorial/intent-grid.png)

## Add an utterance

Now, you can select the intent and click the "Go to Utterances" button on the bottom to create utterances in the intent.
You will see this page:

![Utterances-tab view](media/intent-classifier-tutorial/utterances-tab.png)

To add a new utterance, you can click the 'Add' button on the toolbar, then you will see this view:

![Add-utterance view](media/intent-classifier-tutorial/add-utterance.png)

You can type in an utterance that you come up with, after this, a query will be shown on the bottom where you can add the annotations. 

There are two types of annotations: ```Named entity``` and ```Other```. For example, you can annotate 'London' or 'Bill Gates' as ```Named entity```. For ```Other```, it is for primitive type or custom tag.

To add an annotation, you can select the words by clicking them, you may select multiple at once to annotate. Then you will see the radio buttons.

![Add-utterance-radio-buttons view](media/intent-classifier-tutorial/add-utterance-radio-buttons.png)

For example, we are annotating 'San Francisco'. We can select ```Named entity``` and then choose the corresponding 'Entity type' from your published ontology. 

![Add-utterance-named-entity view](media/intent-classifier-tutorial/add-utterance-named-entity.png)

For custom tag, you can either choose from the history list or add a new one by clicking 'Add custom tag':

![Add-utterance-custom-tag view](media/intent-classifier-tutorial/add-utterance-custom-tag.png)

After annotating, you will see the view below. If you want to change the annotating, you can delete the annotation in the 'Summary' section and annotate again by following the steps above. If your annotating is completed, you can click the 'Save' button on the bottom.

![Add-utterance-completed view](media/intent-classifier-tutorial/add-utterance-completed.png)

## Train, validate, and publish the model

Once you have created intents and utterances, you can go to the "Train & validate" tab to start training the model.

The top panel displays the metrics that summarized the current status for intents and utterances. 

![Intent classifier summary metrics](./media/intent-classifier-tutorial/ic-summary-metrics.png)

You can click on either "Fast train model" or "Full train model" button under the metrics to start training. It may take several minutes to finish the training. You can click the "Refresh model status" button to refresh the current model status.

> The difference between "Fast train model" and "Full train model":<br />
> Fast train model: mainly for quick fixing of DSAT, resulting model is less flexible and requires strict match to utterance to correctly interpret; 
> Full train model: resulting model is able to handle unseen mentions and variations in utterance, model is more versatile and flexible

After the training is completed, a search box will emerge. You can enter utterance that you created before or some similar sentences to validate the trained model. For example, you can enter "find customers in Los Angeles" in the search box and click the "Search" button, the validate result will show up under the search box. 

![Intent classifier model validation](./media/intent-classifier-tutorial/validate-model.png)

You can keep adding more utterances and do another training to improve the model and validate it again.

Once you are satisfied with the results, you can click on the "Publish" button at bottom to make the model live.

## Check the history of models

Under the "History" tab, you can check the training and publishing history for intent classifier models. An example for the history grid is showing as below:

![Intent Classifier History grid](./media/intent-classifier-tutorial/icModel-history-grid.png)

## Manage customized tags

Under the 'Tags' tab, you can manage all of your customized tags. For adding a new tag, besides doing it under this 'Tags' tab, you can also do it in-place when you create new utterance.

> [!IMPORTANT]
> If you delete a tag that is being used in utterances, the corresponding annoataion tag will be removed from the affected utterances as well.
> Similarly, if you edit a tag that is being used in utterances, the corresponding annoataion tag will be updated automatically.