---
swagger: "2.0"
x-collection-name: Google Stackdriver Monitoring
x-complete: 0
info:
  title: Google Stackdriver Monitoring Get Controller Debuggees Debuggeeid Breakpoints
  description: Returns the list of all active breakpoints for the debuggee. The breakpoint
    specification (location, condition, and expression fields) is semantically immutable,
    although the field values may change. For example, an agent may update the location
    line number to reflect the actual line where the breakpoint was set, but this
    doesn't change the breakpoint semantics. This means that an agent does not need
    to check if a breakpoint has changed when it encounters the same breakpoint on
    a successive call. Moreover, an agent should remember the breakpoints that are
    completed until the controller removes them from the active list to avoid setting
    those breakpoints again.
  version: 1.0.0
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /v2/controller/debuggees/register:
    post:
      summary: Post Controller Debuggees Register
      description: Registers the debuggee with the controller service. All agents
        attached to the same application should call this method with the same request
        content to get back the same stable `debuggee_id`. Agents should call this
        method again whenever `google.rpc.Code.NOT_FOUND` is returned from any controller
        method. This allows the controller service to disable the agent or recover
        from any data loss. If the debuggee is disabled by the server, the response
        will have `is_disabled` set to `true`.
      operationId: clouddebugger.controller.debuggees.register
      x-api-path-slug: v2controllerdebuggeesregister-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Debugger
  /v2/controller/debuggees/{debuggeeId}/breakpoints:
    get:
      summary: Get Controller Debuggees Debuggeeid Breakpoints
      description: Returns the list of all active breakpoints for the debuggee. The
        breakpoint specification (location, condition, and expression fields) is semantically
        immutable, although the field values may change. For example, an agent may
        update the location line number to reflect the actual line where the breakpoint
        was set, but this doesn't change the breakpoint semantics. This means that
        an agent does not need to check if a breakpoint has changed when it encounters
        the same breakpoint on a successive call. Moreover, an agent should remember
        the breakpoints that are completed until the controller removes them from
        the active list to avoid setting those breakpoints again.
      operationId: clouddebugger.controller.debuggees.breakpoints.list
      x-api-path-slug: v2controllerdebuggeesdebuggeeidbreakpoints-get
      parameters:
      - in: path
        name: debuggeeId
        description: Identifies the debuggee
      - in: query
        name: successOnTimeout
        description: If set to `true`, returns `google
      - in: query
        name: waitToken
        description: A wait token that, if specified, blocks the method call until
          the list of active breakpoints has changed, or a server selected timeout
          has expired
      responses:
        200:
          description: OK
      tags:
      - Debugger
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---