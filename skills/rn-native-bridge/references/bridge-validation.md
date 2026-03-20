# Bridge Validation

Use this before closing a bridge-related task.

## Validate these explicitly

- API shape on the RN side
- API shape on Android
- API shape on iOS
- generated code if TurboModule or Fabric is involved
- backward compatibility for event names and payload shapes
- command ordering assumptions
- sizing behavior if layout-related fields changed

## Report clearly

- what changed in the contract
- whether any call sites must change
- whether Android and iOS still behave the same
- whether any timing-sensitive path remains unverified
