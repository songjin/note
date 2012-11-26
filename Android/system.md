### 发送短信

 
    private void sendSMS(String message, String phoneNumber) {
        SmsManager sms = SmsManager.getDefault();
        List<String> texts = sms.divideMessage(message);

        for (String text : texts) {
            sms.sendTextMessage(phoneNumber, null, message, null, null);
            Log.i("sms", "send a message");
        }
    }
    