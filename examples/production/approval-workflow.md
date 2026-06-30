# Approval Workflow

Approval pages need history, current state, and irreversible action handling.

```tsx
import { Button, Form, Input, Modal, Steps, Timeline } from 'antd'

export const ApprovalPanel = ({
  currentStep,
  onApprove,
  onReject,
}: {
  currentStep: number
  onApprove: (comment?: string) => Promise<void>
  onReject: (reason: string) => Promise<void>
}) => (
  <>
    <Steps current={currentStep} items={[{ title: 'Submit' }, { title: 'Review' }, { title: 'Done' }]} />
    <Timeline items={[]} />
    <Button type="primary" onClick={() => Modal.confirm({ title: 'Approve request?', onOk: () => onApprove() })}>
      Approve
    </Button>
    <Button
      danger
      onClick={() => {
        Modal.confirm({
          title: 'Reject request?',
          content: (
            <Form layout="vertical">
              <Form.Item label="Reason" required>
                <Input.TextArea />
              </Form.Item>
            </Form>
          ),
          onOk: async () => onReject(''),
        })
      }}
    >
      Reject
    </Button>
  </>
)
```

Production notes:

- Use a real form instance for reject reason collection in production code.
- Show approval history, operator, time, comments, and attachments.
- Disable actions when the current user cannot operate on the current state.
- Make irreversible actions explicit.

