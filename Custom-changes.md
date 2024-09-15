## REPORT TAB IN MOBILE INSIDE VIEWPORT

Replace const navTabs with this, inside MobileNavTabs.tsx inside mobile component:

```
  const navTabs = [
    {
      name: 'Budget',
      path: '/budget',
      style: navTabStyle,
      Icon: SvgWallet,
    },
    {
      name: 'Reports',
      path: '/reports',
      style: navTabStyle,
      Icon: SvgReports,
    },
    {
      name: 'Accounts',
      path: '/accounts',
      style: navTabStyle,
      Icon: SvgPiggyBank,
    },
    {
      name: 'Transaction',
      path: '/transactions/new',
      style: navTabStyle,
      Icon: SvgAdd,
    },
    {
      name: 'Schedules (Soon)',
      path: '/schedules/soon',
      style: navTabStyle,
      Icon: SvgCalendar,
    },
    {
      name: 'Payees (Soon)',
      path: '/payees/soon',
      style: navTabStyle,
      Icon: SvgStoreFront,
    },
    {
      name: 'Rules (Soon)',
      path: '/rules/soon',
      style: navTabStyle,
      Icon: SvgTuning,
    },
    {
      name: 'Settings',
      path: '/settings',
      style: navTabStyle,
      Icon: SvgCog,
    },
  ].map(tab => <NavTab key={tab.path} {...tab} />);
```

##  MORE WIDTH FOR CATEGORY NAMES

In BudgetTotals.tsx:
```
      <View
        style={{
          width: 300,
```

In SidebarCategory.tsx:
```
      style={{
        width: 300,
        overflow: 'hidden',
```

In SidebarGroup.tsx:
```
        ...style,
        width: 300,
        backgroundColor: theme.tableRowHeaderBackground,
```


##  REDESIGN FOR MOBILE

In Components/Mobile/Budget/BudgetTable.jsx:

```
const PILL_STYLE = {
  // borderRadius: 16,
  // color: theme.pillText,
  // backgroundColor: theme.pillBackgroundLight,
};
```

In Components/Common/Card.jsx:

```
export const Card = forwardRef<HTMLDivElement, CardProps>(
  ({ children, ...props }, ref) => {
    return (
      <View
        {...props}
        ref={ref}
        style={{
          marginTop: 15,
      //      marginLeft: 5,
      //    marginRight: 5,
      //    borderRadius: 6,
          backgroundColor: theme.cardBackground,
          borderColor: theme.cardBorder,
      //     boxShadow: '0 1px 2px #9594A8',
          ...props.style,
        }}
      >
        <View
          style={{
            borderRadius: 6,
            overflow: 'hidden',
          }}
        >
          {children}
        </View>
      </View>
    );
  },
);
```


## CASHFLOW THIS MONTH BY DEFAULT (NOT SURE IT'S NEEDED)

In CashFlow.tsx replace the following:
```
  const [start, setStart] = useState(monthUtils.currentMonth() + '-01');
  const [end, setEnd] = useState(monthUtils.currentDay());
  const [showBalance, setShowBalance] = useState(true);
```


In CashFlowCard.tsx, replace the following:
```
  const end = monthUtils.currentDay();
  const start = monthUtils.currentMonth() + '-01';
```

## CHANGE COLOR OF BACKGROUND WHEN IN OTHER MONTH (NOT CURRENT MONTH)

In themes/light.ts:
```
export const budgetOtherMonth = colorPalette.gray100;
```
