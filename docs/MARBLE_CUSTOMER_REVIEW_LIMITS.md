# Card review on Android

Keep card holds disabled on every profile that serves the Android SDK. Passive shadow runs on the Hyperswitch server. Customers keep their usual payment flow during the pilot.

The full SDK at `7f7374d4df5d5a65cd52a40551ada4b303e54c9d` uses Client Core revision `0b69d0b8083960f3320b3230ba45c386e83c5682`. Its payment hooks use the v1 status API. Android Lite loads a separately hosted Web SDK. Each delivery path needs its own verification before enabling card holds.

For a future hold, a v2 confirm response with status 412 should prompt one read of the original payment using the original payment credential and merchant, profile and tenant context. Show “Payment under review” only when the read confirms that state. Show when the status was checked. If the read fails or the outcome is unknown, tell the customer to check the existing payment before paying again. A second tap must return a result to the host app without submitting another payment.

Check these cases on the actual Android build, including a change of merchant or tenant while a status read is in progress. Review and release decisions belong to authorized Hyperswitch operators.
