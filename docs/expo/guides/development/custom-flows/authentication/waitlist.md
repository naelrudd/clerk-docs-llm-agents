# Build a custom waitlist form

> This guide is for users who want to build a custom flow. To use a _prebuilt_ UI, use the [Account Portal pages](https://clerk.com/docs/guides/account-portal/overview.md?sdk=expo) or [prebuilt components](https://clerk.com/docs/expo/reference/components/overview.md).

Clerk's [<Waitlist />](https://clerk.com/docs/expo/reference/components/authentication/waitlist.md) component provides an out-of-the-box solution for allowing users to join your waitlist for early access to your app. However, if you're building a custom user interface, you can use the [useWaitlist()](https://clerk.com/docs/expo/reference/hooks/use-waitlist.md) hook to build a custom waitlist form.

This guide demonstrates how to use the Clerk API to build a custom user interface for joining your app's waitlist.

## Before you start

Before using the `useWaitlist()` hook, you must enable **Waitlist** mode in the Clerk Dashboard:

1. In the Clerk Dashboard, navigate to the [**Waitlist**](https://dashboard.clerk.com/~/user-authentication/waitlist) page.
2. Toggle on **Enable waitlist** and select **Save**.

## Build the custom flow

The following example demonstrates how to use the `useWaitlist()` hook to create a custom waitlist form. Users can submit their email address to join the waitlist, and the component displays appropriate feedback based on the submission state.

filename: src/app/(auth)/waitlist.tsx
```tsx
import { useWaitlist } from '@clerk/expo'
import { useState } from 'react'
import { View, Text, TextInput, Button, StyleSheet } from 'react-native'

export default function WaitlistScreen() {
  const { waitlist, errors, fetchStatus } = useWaitlist()
  const [emailAddress, setEmailAddress] = useState('')

  const handleSubmit = async () => {
    const { error } = await waitlist.join({ emailAddress })
    if (error) {
      console.error('Failed to join waitlist:', error)
    }
  }

  if (waitlist.id) {
    return (
      <View style={styles.container}>
        <Text style={styles.title}>Successfully joined the waitlist!</Text>
        <Text style={styles.message}>We'll notify you when you're approved.</Text>
      </View>
    )
  }

  return (
    <View style={styles.container}>
      <Text style={styles.title}>Join the Waitlist</Text>
      <TextInput
        style={styles.input}
        placeholder="Email address"
        value={emailAddress}
        onChangeText={setEmailAddress}
        keyboardType="email-address"
        autoCapitalize="none"
        autoComplete="email"
      />
      {errors.fields.emailAddress && (
        <Text style={styles.error}>{errors.fields.emailAddress.longMessage}</Text>
      )}
      <Button
        title={fetchStatus === 'fetching' ? 'Submitting...' : 'Join Waitlist'}
        onPress={handleSubmit}
        disabled={fetchStatus === 'fetching'}
      />
    </View>
  )
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 20,
    justifyContent: 'center',
  },
  title: {
    fontSize: 24,
    fontWeight: 'bold',
    marginBottom: 20,
  },
  message: {
    fontSize: 16,
    color: '#666',
  },
  input: {
    borderWidth: 1,
    borderColor: '#ccc',
    borderRadius: 5,
    padding: 10,
    marginBottom: 10,
  },
  error: {
    color: 'red',
    marginBottom: 10,
  },
})
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
