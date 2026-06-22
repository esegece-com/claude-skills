# TsgcHTTPGoogleCloud_PubSub_Client - Example

Usage of `TsgcHTTPGoogleCloud_PubSub_Client` extracted from the **20.HTTP_Protocol/03.Google/01.Google_PubSub** demo. See the full project for context.

API reference: [TsgcHTTPGoogleCloud_PubSub_Client](../reference/api/TsgcHTTPGoogleCloud_PubSub_Client.md)
Source demo: `20.HTTP_Protocol/03.Google/01.Google_PubSub` (file `FGooglePubSub.pas`)

```pascal
procedure TFRMGooglePubSub.btnAcknowledgeClick(Sender: TObject);
  begin
  DoAuthenticate;
  
  DoLog('#Acknowledge', GooglePubSub.Acknowledge
  (txtSubscriberProject.Text, txtSubscriberSubscription.Text,
  txtAckId.Text));
  end;

procedure TFRMGooglePubSub.btnCreateSubscriptionClick(Sender: TObject);
  begin
  DoAuthenticate;
  
  DoLog('#CreateSubscription', GooglePubSub.CreateSubscription
  (txtSubscriberProject.Text, txtSubscriberSubscription.Text,
  txtSubscriberTopic.Text));
  end;

procedure TFRMGooglePubSub.btnCreateTopicClick(Sender: TObject);
  begin
  DoAuthenticate;
  
  DoLog('#CreateTopic', GooglePubSub.CreateTopic(txtPublisherProject.Text,
  txtPublisherTopic.Text));
  end;

procedure TFRMGooglePubSub.btnDeleteSubscriptionClick(Sender: TObject);
  begin
  DoAuthenticate;
  
  DoLog('#DeleteSubscription', GooglePubSub.DeleteSubscripton
  (txtSubscriberProject.Text, txtSubscriberSubscription.Text));
  end;

procedure TFRMGooglePubSub.btnDeleteTopicClick(Sender: TObject);
  begin
  DoAuthenticate;
  
  DoLog('#DeleteTopic', GooglePubSub.DeleteTopic(txtPublisherProject.Text,
  txtPublisherTopic.Text));
  end;

procedure TFRMGooglePubSub.btnGetSubscriptionClick(Sender: TObject);
  begin
  DoAuthenticate;
  
  DoLog('#GetSubscription',
  GooglePubSub.GetSubscription(txtSubscriberProject.Text,
  txtSubscriberSubscription.Text));
  end;

procedure TFRMGooglePubSub.btnGetTopicClick(Sender: TObject);
  begin
  DoAuthenticate;
  
  DoLog('#GetTopic', GooglePubSub.GetTopic(txtPublisherProject.Text,
  txtPublisherTopic.Text));
  end;

procedure TFRMGooglePubSub.btnListSubscriptionsClick(Sender: TObject);
```

