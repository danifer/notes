Mail Sieve email filtering rules for forwarding, redirecting, and copying messages to multiple recipients.

#Send a copy of an email to another recipient:

  if address :is "to" "mail@example.com" {
    redirect "recipient@example.com";
    keep;
  }
