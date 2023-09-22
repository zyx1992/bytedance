## React ErrorBoundary

```react
interface ErrorBoundaryProps {
  children?: ReactNode;
}
interface ErrorBoundaryState {
  readonly error?: unknow;
  readonly id?: string;
  readonly tipVisible?: boolean;
}
export class SilenceErrorBoundary extends Compnent<ErrorBoundaryProps, SilenceErrorBoundaryState> {
  protected static getDerivedStateFromError(error: unknow): SilenceErrorBoundaryState {
    return {error, id: createErrorId(), tipVisible: true }
  }

  public state: = {}

  public componentDidCatch(error:unknow, errorInfo: ErrorInfo) {
    const {id} = this.state;
    slardar('captureException', error, id? {id}: {}, {version, ...errorInfo})
  }

  public render() {
    const {children} = this.props;
    const {error, id, tipVisible} = this.state;

    // return id && tipVisible ? (<ErrorBoundaryTip error={error} errorId= {id} onClose={this.#onCloseTip} />) : children;
    return id ? null : children;
  }
}

function createErrorId():string {
  const timestamp = dayjs().format('YYYYMMDDHHmm')
  const salt = `${randomInt(0, 9999_9999)}`.padStart(8, '0')
  return `${timestamp}${salt}`;
}

```
